# Initial Development Machine Setup on Ubuntu 22.04

This playbook will execute a initial development machine setup for Ubuntu 22.04 systems.
A number of containers will be created with the options specified in the `vars/default.yml` variable file.

## Settings

- `create_user`: the name of the remote sudo user to create.
- `copy_local_key`: path to a local SSH public key that will be copied as authorized key for the new user. By default, it copies the key from the current system user running Ansible.
- `sys_packages`: array with list of packages that should be installed.


## Running this Playbook

Quick Steps:

### 1. Obtain the playbook
```shell
git clone https://github.com/do-community/ansible-playbooks.git
cd ansible-playbooks/setup_ubuntu1804
```

### 2. Customize Options

```shell
nano vars/default.yml
```

```yml
#vars/default.yml
---
create_user: sammy
copy_local_key: "{{ lookup('file', lookup('env','HOME') + '/.ssh/id_rsa.pub') }}"
sys_packages: [ 'curl', 'vim', 'git', 'ufw']
```

### 3. Run the Playbook

```command
ansible-playbook -l [target] -i [inventory file] -u [remote user] playbook.yml
```
