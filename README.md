# prometheus_phpfpm_exporter

Master: [![Build Status](https://travis-ci.org/sansible/prometheus_phpfpm_exporter.svg?branch=master)](https://travis-ci.org/sansible/prometheus_phpfpm_exporter)  
Develop: [![Build Status](https://travis-ci.org/sansible/prometheus_phpfpm_exporter.svg?branch=develop)](https://travis-ci.org/sansible/prometheus_phpfpm_exporter)

* [ansible.cfg](#ansible-cfg)
* [Installation and Dependencies](#installation-and-dependencies)
* [Tags](#tags)
* [Examples](#examples)

This roles installs Prometheus PHP FPM Exporter.

Prometheus PHP FPM Exporter makes available PHP FPM metrics for collection by Prometheus server.

For more information about Prometheus PHP FPM Exporter please visit
[https://github.com/bakins/php-fpm-exporter](https://github.com/bakins/php-fpm-exporter).

For more information about Prometheus Server please visit
[https://prometheus.io](https://prometheus.io).


## ansible.cfg

This role is designed to work with merge "hash_behaviour". Make sure your
ansible.cfg contains these settings

```INI
[defaults]
hash_behaviour = merge
```




## Installation and Dependencies

This role will install `sansible.users_and_groups` for managing `prometheus_phpfpm_exporter` user.

To install run `ansible-galaxy install sansible.prometheus_phpfpm_exporter` or add this to your
`roles.yml`.

```YAML
- name: sansible.prometheus_phpfpm_exporter
  version: v1.0
```

and run `ansible-galaxy install -p ./roles -r roles.yml`




## Tags

This role uses tags: **build** and **configure**

* `build` - Installs Prometheus PHP FPM Exporter and all it's dependencies.




## Examples

Simply include role in your playbook accepting the defaults:

exporter address 0.0.0.0:9338 

PHP FPM endpoint http://127.0.0.1:80/status

```YAML
- name: Install and configure prometheus_phpfpm_exporter
  hosts: "{{ host }}"

  roles:
    - role: sansible.prometheus_phpfpm_exporter
```

Include the role in your playbook overriding the exporter address and the PHP endpoint:

```YAML
- name: Install and configure the prometheus_phpfpm_exporter
  hosts: "{{ host }}

  roles:
    - role: sansible.prometheus_phpfpm_exporter
      prometheus_phpfpm_exporter:
        opts: --addr 0.0.0.0:1234 --endpoint http://127.0.0.1:8080/status
```
    
```YAML
- name: Install, configure and start on boot prometheus_phpfpm_exporter
  hosts: "{{ host }}

  roles:
    - role: sansible.prometheus_phpfpm_exporter
      prometheus_phpfpm_exporter:
        start_on_boot: yes
        opts: --addr 0.0.0.0:1234 --endpoint http://127.0.0.1:8080/status
```
