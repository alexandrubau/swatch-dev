# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

    config.vm.define "swatch" do |swatch|
        swatch.vm.box       = "bento/ubuntu-18.04"
        swatch.vm.hostname  = "swatch.local"
        swatch.vm.network "private_network", ip: "192.168.13.37"
        swatch.vm.synced_folder "./", "/vagrant"
    end

    config.vm.provider "virtualbox" do |vbox|
        vbox.memory = 512
        vbox.cpus   = 1
    end

    config.vm.provision "shell", path: "Vagrantboot"

    config.vm.provision "ansible_local" do |ansible|
        ansible.inventory_path    = "inventories/dev/hosts"
        ansible.playbook          = "provision.yml"
        ansible.limit             = "all"
    end
end
