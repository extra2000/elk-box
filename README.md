# elk-box

| License | Versioning | Build |
| ------- | ---------- | ----- |
| [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) | [![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release) | [![Build status](https://ci.appveyor.com/api/projects/status/aciapusi512qm485/branch/master?svg=true)](https://ci.appveyor.com/project/nikAizuddin/elk-box/branch/master) |

Developer box for ELK (Elasticsearch, Logstash, Kibana) stack.


## Creating Vagrant Box

Copy example pillar file for ELK Stack. Optionally you may want to edit the values in the `elk.sls`:
```
$ cp -v salt/roots/pillar/podman.sls.example salt/roots/pillar/podman.sls
$ cp -v salt/roots/pillar/elk.sls.example salt/roots/pillar/elk.sls
$ cp -v salt/roots/pillar/nginx.sls.example salt/roots/pillar/nginx.sls
$ cp -v salt/roots/pillar/zabbix-agent.sls.example salt/roots/pillar/zabbix-agent.sls
```

Copy vagrant file from `vagrant/examples/` and then create the vagrant box (you can change to `--provider=libvirt` if you want to use Libvirt provider):
```
$ cp -v vagrant/examples/Vagrantfile.elk-box.fedora-34.x86_64.example vagrant/Vagrantfile.elk-box
$ vagrant up --provider=virtualbox
```

Provision the vagrant box:
```
$ vagrant ssh elk-box -- sudo salt-call state.highstate
```

Configure ELK and NGINX:
```
$ vagrant ssh elk-box -- sudo salt-call state.sls elk.config
$ vagrant ssh elk-box -- sudo salt-call state.sls elk.config.nginx,nginx.service
```


## Deploying Elasticsearch

Deploy Elasticsearch. Then, set usernames and passwords:
```
$ vagrant ssh elk-box -- sudo salt-call state.sls elk.service.elasticsearch
$ vagrant ssh elk-box -- podman exec -it elk-elasticsearch-pod-es01 elasticsearch-setup-passwords interactive
```

For testing purpose, use password `abcde12345` for all services as listed below. Please change to a secure password for production:
* `elastic`
* `apm_system`
* `kibana_system`
* `logstash_system`
* `beats_system`
* `remote_monitoring_user`


## Setup Templates

Setup Filebeat template:
```
$ vagrant ssh elk-box -- podman run --rm --pod elk-elasticsearch-pod --env ELASTICSEARCH_USERNAME='elastic' --env ELASTICSEARCH_PASSWORD='abcde12345' --privileged docker.elastic.co/beats/filebeat:7.12.1 setup --index-management -E output.logstash.enabled=false -E 'output.elasticsearch.hosts=["127.0.0.1:9200"]'
```

Setup Metricbeat template:
```
$ vagrant ssh elk-box -- podman run --rm --pod elk-elasticsearch-pod --env ELASTICSEARCH_USERNAME='elastic' --env ELASTICSEARCH_PASSWORD='abcde12345' docker.elastic.co/beats/metricbeat:7.12.1 setup --index-management -E output.logstash.enabled=false -E 'output.elasticsearch.hosts=["127.0.0.1:9200"]'
```

Setup Packetbeat template:
```
$ vagrant ssh elk-box -- podman run --rm --pod elk-elasticsearch-pod --env ELASTICSEARCH_USERNAME='elastic' --env ELASTICSEARCH_PASSWORD='abcde12345' --privileged docker.io/elastic/packetbeat:7.12.1 setup --index-management -E output.logstash.enabled=false -E 'output.elasticsearch.hosts=["127.0.0.1:9200"]'
```


## Deploying Kibana

Deploy Kibana:
```
$ vagrant ssh elk-box -- sudo salt-call state.sls elk.service.kibana
```


## Configuring Kibana

Login Kibana as `superuser` role, go to https://elk-box and use the following login:
* Username: `elastic`
* Password: `abcde12345`

Create a minimal space such as removing unused Kibana features. Go to `Stack Management` > `Kibana` > `Spaces` and create a space named `minimal` with the following features only:
* Kibana:
    * Discover
    * Dashboard
    * Visualize
* Observability:
    * Logs
    * Metrics
* Management:
    * Index Pattern Management
    * Advanced Settings

Create a Kibana admin. Go to `Stack Management` > `Security` > `Users` and for example create a new user named `kadmin` with role `kibana_admin`.

To create a Kibana read-only user, a custom read-only role named `user` must be created first. Go to `Stack Management` > `Security` > `Role` and `Create role` with the following information:
* Role name: `user`
* Index privileges:
    * Indices: `filebeat-*`, `winlogbeat-*`, `metricbeat-*`, `packetbeat-*`, Privileges: `read`
* Add Kibana privileges:
    * Spaces: `minimal`
    * Privileges for all features: `Read`

Go to `Stack Management` > `Security` > `Users` and create a new username with role `user`.

To prevent Kibana error `Unable to update ui setting, error code 403` for read-only users, go to `Stack Management` > `Index patterns` and set an `index` as default.


## Configuring Elasticsearch for Logstash permissions

Go to `Stack Management` > `Security` > `Role` and `Create role` to create a new role named `logstash_writer` with the following information:
* Role name: `logstash_writer`
* Cluster privileges:
    * `manage_index_templates`
    * `monitor`
    * `manage_ilm`
* Index privileges:
    * Indices: `logstash-*`, `filebeat-*`, `winlogbeat-*`, `metricbeat-*`, `packetbeat-*`, Privileges: `write`, `create`, `create_index`, `manage`, `manage_ilm`.

Create a new user named `logstash_internal` with role `logstash_writer`. Use password `abcde12345`.


## Deploying Logstash

Define pipelines file `salt/roots/formulas/elk-formula/elk/files/pipelines.yml`:
```
- pipeline.id: main
  path.config: "/usr/share/logstash/pipeline/logstash.conf"

- pipeline.id: csv
  path.config: "/usr/share/logstash/pipeline/csv.conf"

- pipeline.id: output
  path.config: "/usr/share/logstash/pipeline/output.conf"
```

Create pipeline file `salt/roots/formulas/elk-formula/elk/files/pipelines/logstash.conf`:
```
input {
  beats {
    port => 5044
  }
}

output {
  pipeline {
    send_to => [
      "pipeline-csv"
    ]
  }
}
```

Create pipeline file `salt/roots/formulas/elk-formula/elk/files/pipelines/csv.conf`:
```
input {
  pipeline {
    address => "pipeline-csv"
  }
}

filter {
  if [fields][testlog] {
    csv {
      autogenerate_column_names => false
      columns => ["training.epoch", "training.accuracy"]
    }
    mutate {
      convert => {
        "training.epoch" => "integer"
        "training.accuracy" => "float"
      }
    }
  }
}

output {
  pipeline {
    send_to => ["pipeline-output"]
  }
}
```

Create pipeline file `salt/roots/formulas/elk-formula/elk/files/pipelines/output.conf`:
```
input {
  pipeline {
    address => "pipeline-output"
  }
}

output {
  elasticsearch {
    hosts => ['http://elk-elasticsearch-pod:9200']
    index => "%{[@metadata][beat]}-%{[@metadata][version]}-%{+YYYY.MM.dd}"
    user => "logstash_internal"
    password => "abcde12345"
  }
}
```

Deploy Logstash:
```
$ vagrant rsync
$ vagrant ssh elk-box -- sudo salt-call state.sls elk.config
$ vagrant ssh elk-box -- sudo salt-call state.sls elk.service.logstash
```


## Create systemd units for auto startup on boot

Generate systemd units for ELK pods and enable them:
```
$ cd ~/.config/systemd/user
$ podman generate systemd --files --name elk-elasticsearch-pod
$ podman generate systemd --files --name elk-logstash-pod
$ podman generate systemd --files --name elk-kibana-pod
$ systemctl --user enable pod-elk-elasticsearch-pod.service container-elk-elasticsearch-pod-es01.service pod-elk-logstash-pod.service container-elk-logstash-pod-ls01.service pod-elk-kibana-pod.service container-elk-kibana-pod-k01.service
```

Generate systemd unit for `nginx-pod` and enable it:
```
$ cd ~/.config/systemd/user
$ podman generate systemd --files --name nginx-pod
$ systemctl --user enable pod-nginx-pod.service container-nginx-pod-srv01.service
```

Generate systemd unit for `zabbix-agent-pod` and enable it:
```
$ cd ~/.config/systemd/user
$ podman generate systemd --files --name zabbix-zabbix-agent-pod
$ systemctl --user enable pod-zabbix-zabbix-agent-pod.service container-zabbix-zabbix-agent-pod-agent.service
```


## Database management

To delete documents by query:
```
$ curl --user elastic:abcde12345 -X POST "localhost:9200/winlogbeat-*/_delete_by_query?pretty" -H 'Content-Type: application/json' -d'
{
  "query": {
    "match": {
      "event.provider": "Service Control Manager"
    }
  }
}
'
```

To delete all documents in an index:
```
$ curl --user elastic:abcde12345 -X DELETE "localhost:9200/winlogbeat-*?pretty"
```
