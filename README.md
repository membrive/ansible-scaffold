# ansible-scaffold

An scaffold for Ansible projects with Vagrant support.

## Requirements

- Ansible
- Virtualbox and Vagrant (for `vagrant/` features)

## Roles management

Include your requirements in `roles/requirements.yml` and install them with `ansible-galaxy install -r roles/requirements.yml --roles-path roles/external`. In this way you only have to commit the `roles/requirements.yml` file.

## Local development with Vagrant and Virtualbox

Easy way:

```
cd vagrant
vagrant up
```

You can configure the Ansible behaviour the virtual machines parameters in the file `vagrant/machines.yml`, for example:

```YAML
---
- name: vagrant01
  box: ubuntu/xenial64
  box_version: "v20180510.0.0"
  memory: 1024
  cpus: 1
  ip: 172.28.128.2
  ansible_playbook: ../playbook.yml
  ansible_tags:
    - nginx
    - nodejs

- name: vagrant02
  box: ubuntu/trusty64
  memory: 512
  cpus: 1
  ip: 172.28.128.3
  ansible_playbook: ../playbook2.yml
```

In order to provision the existing Vagrant machines, you can run `vagrant up --provision`.


## License

MIT / BSD

## Author

Created and maintained by [Fernando Membrive](https://membrive.net).