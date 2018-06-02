# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.1"

  # network
  config.vm.network "private_network", ip: "192.168.33.10"

  # provision
  config.vm.provision :ansible_local do |ansible|
    ansible.install = true
    ansible.playbook = 'playbook.yml'
    ansible.provisioning_path = '/vagrant/provision'
    ansible.become_user = 'root'
    ansible.become = true
  end
end
