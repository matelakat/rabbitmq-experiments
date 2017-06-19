# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

VARS = YAML.load_file('vars.yml')
NODES = VARS['nodes']
BRIDGE_NAME = VARS['network']['bridge_name']

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.box = "suse/sles12sp1"
  config.vm.box_check_update = false
  config.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yaml"
  end

  NODES.each do |address, node_name|
    config.vm.define node_name do |node_vm|
        node_vm.vm.network "public_network", ip: address, bridge: BRIDGE_NAME
        node_vm.vm.hostname = node_name

        node_vm.vm.provider "virtualbox" do |vb|
          vb.gui = false
          vb.name = node_name
          vb.memory = 1024
          vb.cpus = 1
       end
    end
  end
end
