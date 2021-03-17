# Changelog

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
