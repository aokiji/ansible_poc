# Ansible PoC

Provision a virtual machine using ansible locally

## Getting started

Just fire up vagrant

```
vagrant up
```

This will create the virtual machine and provision it.

If you make changes to the provisioning and wish to redo it, then

```
vagrant provision
```

## Setup

in provision/playbook.yml are the recipies executed on the minions, place there your configuration.

for example for installing vim you would include in your playbook.yml file the following

```yaml
# provision/playbook.yml
---
- hosts: all
  roles:
    - vim
```

And setup a vim role

```yaml
# provision/roles/vim/tasks/main.yml
- name: Install vim
  yum:
    name: vim-enhanced
    state: latest
```

## Advice

Sometimes it may be useful to start at a certain task for debug purposes, to accomplish this
just modify your Vagranfile such as:

```ruby
# Vagranfile
config.vm.provision :ansible_local do |ansible|
  # ... ansible config
  ansible.raw_arguments = '--start-at-task="Install vim"'
end
```

and then run the provision command.
