# elk-box

| License | Versioning | Build |
| ------- | ---------- | ----- |
| [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) | [![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release) | [![Build status](https://ci.appveyor.com/api/projects/status/aciapusi512qm485/branch/master?svg=true)](https://ci.appveyor.com/project/nikAizuddin/elk-box/branch/master) |

Developer box for ELK (Elasticsearch, Logstash, Kibana) stack.


## Creating Vagrant Box

Copy example pillar file for ELK Stack. Optionally you may want to edit the values in the `elk.sls`:
```
$ cp -v salt/roots/pillar/elk.sls.example salt/roots/pillar/elk.sls
$ cp -v salt/roots/pillar/nginx.sls.example salt/roots/pillar/nginx.sls
$ cp -v salt/roots/pillar/zabbix-agent.sls.example salt/roots/pillar/zabbix-agent.sls
```

Copy vagrant file from `vagrant/examples/` and then create the vagrant box (you can change to `--provider=libvirt` if you want to use Libvirt provider):
```
$ cp -v vagrant/examples/Vagrantfile.elk-box.fedora-33.x86_64.example vagrant/Vagrantfile.elk-box
$ vagrant up --provider=virtualbox
```

Provision the vagrant box:
```
$ vagrant ssh elk-box -- sudo salt-call state.highstate
```


## Deploying ELK Stack

Configure ELK and NGINX:
```
$ vagrant ssh elk-box -- sudo salt-call state.sls elk.config
$ vagrant ssh elk-box -- sudo salt-call state.sls elk.config.nginx
```

Deploy Elasticsearch. Then, set username and password:
```
$ vagrant ssh elk-box -- sudo salt-call state.sls elk.service.elasticsearch
$ vagrant ssh elk-box -- podman exec -it elasticsearch-pod-es01 elasticsearch-setup-passwords interactive
```

For testing purpose, use password `abcde12345` for all services as listed below. Please change to a secure password for production:
* `elastic`
* `apm_system`
* `kibana_system`
* `logstash_system`
* `beats_system`
* `remote_monitoring_user`

Deploy Logstash and Kibana
```
$ vagrant ssh elk-box -- sudo salt-call state.sls elk.service.logstash
$ vagrant ssh elk-box -- sudo salt-call state.sls elk.service.kibana
```

To access Kibana, go to https://elk-box and use the following login:
* Username: `elastic`
* Password: `abcde12345`