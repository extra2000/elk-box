# Changelog

## [4.0.0](https://github.com/extra2000/elk-box/compare/v3.1.0...v4.0.0) (2021-05-15)


### ⚠ BREAKING CHANGES

* **elk-formula:** submodule `elk-formula` has breaking changes.
* **podman:** File `salt/roots/pillar/podman.sls` has been removed and ignored into `.gitignore`.
* **nginx-formula:** submodule `nginx-formula has breaking changes.
* **podman-formula:** Submodule `podman-formula` has major changes.

### Features

* **elk-formula:** upgrade from `v2.2.0` to `v3.0.0` ([1430771](https://github.com/extra2000/elk-box/commit/14307711cad4fa994bbe0c7860077bfffa739b4e))
* **nginx-formula:** upgrade to `v3.0.0` ([6842894](https://github.com/extra2000/elk-box/commit/68428946386e6d0a5cabccbec6cfb59ae271443e))
* **podman-formula:** Upgrade from `v2.2.2` to `v4.0.0` ([971430f](https://github.com/extra2000/elk-box/commit/971430f4ebe8e442efe42376e914a04e0f47d7aa))
* **zabbix-agent-formula:** upgrade to `v5.0.0` ([861b481](https://github.com/extra2000/elk-box/commit/861b48164c6392f50b665309ddf27d25a0c4c0d5))


### Continuous Integrations

* **AppVeyor:** Add instruction to create `salt/roots/pillar/podman.sls` ([2482e6e](https://github.com/extra2000/elk-box/commit/2482e6e6a878f5c6a01c6e591940512856ba658e))
* **AppVeyor:** Remove NGINX workaround ([341541b](https://github.com/extra2000/elk-box/commit/341541beb1e665ee7baec29a576bdb515427efaf))


### Fixes

* **salt/roots/pillar/elk.sls.example:** Change `cni-podman0` to `cni-podman1` to prevent network conflict with rootful Podman ([be2f67e](https://github.com/extra2000/elk-box/commit/be2f67e58ea133f4dc00617f418bcea4028328f1))


### Code Refactoring

* **podman:** Remove `salt/roots/pillar/podman.sls` and add into `.gitignore` ([a044fa9](https://github.com/extra2000/elk-box/commit/a044fa92a3e1d2a208fac9740173a03bb81cbddc))
* **salt/roots/pillar/elk.sls.example:** Add `projectname`, prefix URL and pod names with `projectname` ([1ad888d](https://github.com/extra2000/elk-box/commit/1ad888dc1161ca53d39f40e5ab2d02ce62c0d0c0))
* **salt/roots/pillar/elk.sls.example:** Add server name for NGINX HTTPS conf files ([ee35518](https://github.com/extra2000/elk-box/commit/ee35518f052485ec113e10400990819d78803850))
* **salt/roots/pillar/elk.sls.example:** Change `podman-cluster` to `elk-clustor` ([55272c5](https://github.com/extra2000/elk-box/commit/55272c53224f374bf77fc46e4d6ae92d18fd584a))


### Documentations

* **podman:** Add `salt/roots/pillar/podman.sls.example` ([927acdd](https://github.com/extra2000/elk-box/commit/927acdd1ab003e1d8017488c4ec845621f473156))
* **README:** Add instruction to create `salt/roots/pillar/podman.sls` ([ab8fe5a](https://github.com/extra2000/elk-box/commit/ab8fe5aa9ee696d6dbfa2d7020ffc640a347edf2))
* **README:** Prefix ELK and Zabbix container names with default `projectname` ([ca984d5](https://github.com/extra2000/elk-box/commit/ca984d500e1f1a91f7518f6343027e272045c97e))
* **README:** Remove `systemctl --user daemon-reload` ([d6a4762](https://github.com/extra2000/elk-box/commit/d6a4762c01dae193a420c72ee0dbd6ea9e03eca7))
* **salt/roots/pillar/zabbix-agent.sls.example:** add `projectname` ([33c3821](https://github.com/extra2000/elk-box/commit/33c38213cc1093d99e3a7d21436b1fecf85b20d6))

## [3.1.0](https://github.com/extra2000/elk-box/compare/v3.0.0...v3.1.0) (2021-04-29)


### Features

* **elk-formula:** Upgrade from `v2.1.0` to `v2.2.0` ([ed1031c](https://github.com/extra2000/elk-box/commit/ed1031c800f803f784b8798f9fe412f7b5706187))
* **vagrant:** Add Fedora 34 `x86_64` Vagrant file ([8a1a125](https://github.com/extra2000/elk-box/commit/8a1a1256120c05b039a1d5dcdbb9c0aa02503150))
* **vagrant:** Upgrade CentOS Stream from `v20201217.0` to `v20210210.0` ([7577143](https://github.com/extra2000/elk-box/commit/757714305cf5c7e5236052e0763163e32802bc53))
* **vagrant:** Upgrade SaltStack from `v3002.2` to `v3003` ([c4b114c](https://github.com/extra2000/elk-box/commit/c4b114c5f292b2455496f5505115377d0013fe33))


### Styles

* **README:** Remove extra spacing ([6d139a0](https://github.com/extra2000/elk-box/commit/6d139a0fd406c0c3bc77029e74ca3715068d2574))


### Fixes

* **podman-formula:** Patch update from `v2.2.1` to [v2.2.2](https://github.com/extra2000/podman-formula/releases/tag/v2.2.2) ([bf9b3e7](https://github.com/extra2000/elk-box/commit/bf9b3e76db9b490819b3d66445baf7ecdce8fbc0))


### Documentations

* **README:** Add `Dashboard` ([da98c68](https://github.com/extra2000/elk-box/commit/da98c682cb8244efed8eac752c6ec11d4756e51f))
* **README:** Add example how to delete document and index ([f1cb17c](https://github.com/extra2000/elk-box/commit/f1cb17c035e720d85f22387d498d1011269a5349))
* **README:** Add instructions for initializing Filebeat template ([351f3ba](https://github.com/extra2000/elk-box/commit/351f3ba45edf4f3a5a9595638bc3bc385d12196d))
* **README:** Add instructions for initializing Metricbeat template ([954c10c](https://github.com/extra2000/elk-box/commit/954c10cb961f23135e4c17758d3f7f53977d41cb))
* **README:** Add instructions for initializing Packetbeat template ([918737d](https://github.com/extra2000/elk-box/commit/918737da72e348322fc5212d8a81d40a8cee9113))
* **README:** Add instructions how to create systemd units for auto startup on boot ([18d089e](https://github.com/extra2000/elk-box/commit/18d089ebc978285242b8e2dface2c1af4db57db1))
* **README:** Add instructions how to fix Kibana `Unable to update ui setting` ([2445a2f](https://github.com/extra2000/elk-box/commit/2445a2fce5ec1f7aac18d0e0724585a03937e846))
* **README:** Set Fedora 34 as default Vagrant instruction ([e1a0cb5](https://github.com/extra2000/elk-box/commit/e1a0cb5879b82aa56c3e4194218e5df796028c9c))

## [3.0.0](https://github.com/extra2000/elk-box/compare/v2.4.0...v3.0.0) (2021-03-17)


### ⚠ BREAKING CHANGES

* **submodule:** Pillar format for `salt/roots/pillar/zabbix-agent.sls.example` has changed.

### Features

* **submodule:** Update `zabbix-agent-formula` to [v4.0.0](https://github.com/extra2000/zabbix-agent-formula/releases/tag/v4.0.0) ([5ad1daa](https://github.com/extra2000/elk-box/commit/5ad1daa602e25d9bfc41a72c32aa0a4962a2b4aa))


### Documentations

* **README:** Add `winlogbeat-*` index ([dd3a38d](https://github.com/extra2000/elk-box/commit/dd3a38dc591c253e1b62f53ec0b521e576165204))
* **vagrant:** Add port forwarding example for Logstash port `5044` ([bd7cd82](https://github.com/extra2000/elk-box/commit/bd7cd82d387e9e44ed83af1f7f45249537d54b2c))

## [2.4.0](https://github.com/extra2000/elk-box/compare/v2.3.0...v2.4.0) (2021-03-15)


### Features

* **submodule:** Upgrade `elk-formula` to version [v2.1.0](https://github.com/extra2000/elk-formula/releases/tag/v2.1.0) ([85ba3b0](https://github.com/extra2000/elk-box/commit/85ba3b054476b75dd30951e73eb61f13bd3986df))


### Documentations

* **README:** Enable `Advanced Settings` in `minimal` space ([c21e986](https://github.com/extra2000/elk-box/commit/c21e986b7247542ee5872557227c5a769f876315))

## [2.3.0](https://github.com/extra2000/elk-box/compare/v2.2.0...v2.3.0) (2021-03-14)


### Features

* **submodule:** Update `elk-formula` to [v2.0.0](https://github.com/extra2000/elk-formula/releases/tag/v2.0.0) ([9086cb4](https://github.com/extra2000/elk-box/commit/9086cb43c1fca3ef923d16878aa3921b07b0d455))
* **submodule:** Update `nginx-formula` to [v2.0.0](https://github.com/extra2000/nginx-formula/releases/tag/v2.0.0) ([9215f60](https://github.com/extra2000/elk-box/commit/9215f60a0ea448d923cb82b7454a9054f8f03cea))


### Continuous Integrations

* **AppVeyor:** Using example NGINX HTTPS conf file to prevent state error ([7161c3a](https://github.com/extra2000/elk-box/commit/7161c3a11306e4f1191f67257e0b29fd31608285))


### Documentations

* **README:** Update instruction for deploying NGINX ([7c368d5](https://github.com/extra2000/elk-box/commit/7c368d5ba4b0b150d32ad41691e11bcdc9bac735))

## [2.2.0](https://github.com/extra2000/elk-box/compare/v2.1.0...v2.2.0) (2021-03-14)


### Features

* **submodule:** Update `elk-formula` to [v1.1.1](https://github.com/extra2000/elk-formula/releases/tag/v1.1.1) which prevent pod networking conflicts ([686d60e](https://github.com/extra2000/elk-box/commit/686d60e74a76fd9c426214a384899904f77decb0))


### Documentations

* **pillar/elk.sls.example:** Add example how to set `bridge` for pod networking ([0e595f6](https://github.com/extra2000/elk-box/commit/0e595f6447402b30fdb7da23c08a5b3ca14e4a28))

## [2.1.0](https://github.com/extra2000/elk-box/compare/v2.0.1...v2.1.0) (2021-03-13)


### Features

* **/etc/minion:** Using new style for `module.run` ([0f8b8f2](https://github.com/extra2000/elk-box/commit/0f8b8f21d67d1ef2bccb66d4e3a8385dcf002521))
* **submodule:** Update `elk-formula` to [v1.1.0](https://github.com/extra2000/elk-formula/releases/tag/v1.1.0) ([daeb651](https://github.com/extra2000/elk-box/commit/daeb651cf918258e9a68f9bff679c4d0d3546135))


### Documentations

* **pillar/elk.sls.example:** Improve security by using non `elastic` user privileges ([bf14651](https://github.com/extra2000/elk-box/commit/bf14651c75e4d33a89d7dd99eb6fb7119faeb10b))
* **README:** Improve deployment instructions and harden security ([1a581e1](https://github.com/extra2000/elk-box/commit/1a581e1de027c064687f284c9ed43ab635e90f93))

### [2.0.1](https://github.com/extra2000/elk-box/compare/v2.0.0...v2.0.1) (2021-03-09)


### Fixes

* **submodule:** Update `zabbix-agent-formula` to [v2.0.1](https://github.com/extra2000/zabbix-agent-formula/releases/tag/v2.0.1) which fixes SELinux permissions ([abcbe49](https://github.com/extra2000/elk-box/commit/abcbe497be411cb634ab32a92b1aabf5940d295d))

## [2.0.0](https://github.com/extra2000/elk-box/compare/v1.0.0...v2.0.0) (2021-03-09)


### ⚠ BREAKING CHANGES

* **submodule, pillar:** Pillar format in `salt/roots/pillar/zabbix-agent.sls.example` has changed.

### Features

* **submodule, pillar:** Update `zabbix-agent-formula` to [v2.0.0](https://github.com/extra2000/zabbix-agent-formula/releases/tag/v2.0.0) ([6052b9f](https://github.com/extra2000/elk-box/commit/6052b9fb667d3a9f4a83102b2f4a62579c5227e5))

## 1.0.0 (2021-03-07)


### Features

* **salt:** Add implementations for `salt/` ([0ec55d1](https://github.com/extra2000/elk-box/commit/0ec55d1c791b15122238fa02e8072805ceee6440))
* **submodule:** Add [elk-formula v1.0.0](https://github.com/extra2000/elk-formula/releases/tag/v1.0.0) ([24daded](https://github.com/extra2000/elk-box/commit/24daded5c3ca426ee690fd845dca9911879b1e74))
* **submodule:** Add [nginx-formula v1.0.1](https://github.com/extra2000/nginx-formula/releases/tag/v1.0.1) ([420bc3f](https://github.com/extra2000/elk-box/commit/420bc3f445f465a52fe34b1261e425a32b34bf7a))
* **submodule:** Add [podman-formula v2.2.1](https://github.com/extra2000/podman-formula/releases/tag/v2.2.1) ([ce3e7e9](https://github.com/extra2000/elk-box/commit/ce3e7e955de50338a2c0b1d9a21f13ec3718a229))
* **submodule:** Add [zabbix-agent-formula v1.0.0](https://github.com/extra2000/zabbix-agent-formula/releases/tag/v1.0.0) ([5b7d84e](https://github.com/extra2000/elk-box/commit/5b7d84e7dac78e3581186d3f19bf0180233e2d83))
* **vagrant:** Import Vagrant files from [extra2000/generic-box v1.5.0](https://github.com/extra2000/generic-box/releases/tag/v1.5.0) ([e6d1ccf](https://github.com/extra2000/elk-box/commit/e6d1ccf0ee9fd0e1c8f76ba3c99eb7415de685b0))


### Continuous Integrations

* Add AppVeyor with `semantic-release` bot ([e20eed9](https://github.com/extra2000/elk-box/commit/e20eed9635b76e0950da27dd39a8e13d8d2511e7))


### Documentations

* **README:** Update `README.md` ([e87d829](https://github.com/extra2000/elk-box/commit/e87d8294082d57096d700547fe36e28eab99a54f))
