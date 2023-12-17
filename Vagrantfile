# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "generic/centos8"
    config.vm.box_version = "4.3.6"
  
    config.vm.define("ds") do |ds|
      ds.vm.hostname = "ds.iservermate.local"
      ds.vm.network "public_network", bridge: "eno1", ip:"192.168.0.51"
      #config.vm.network "public_network"
    end
  
      config.vm.provider "virtualbox" do |vb|
       vb.gui = false
       vb.memory = "2024"
       vb.cpus = "1"
      end
  
    config.vm.provision :ansible do |ansible|
      ansible.playbook = "SystemConfiguration.yml"
    end
    end
  
    ####
    Vagrant.configure("2") do |config|
      config.vm.box = "generic/centos8"
      config.vm.box_version = "4.3.6"
    
      config.vm.define("test") do |test|
        test.vm.hostname = "test.iservermate.local"
        test.vm.network "public_network", bridge: "eno1", ip:"192.168.0.52"
        #config.vm.network "public_network"
      end
    
        config.vm.provider "virtualbox" do |vb|
         vb.gui = false
         vb.memory = "2024"
         vb.cpus = "1"
        end
    
      config.vm.provision :ansible do |ansible|
        ansible.playbook = "SystemConfiguration.yml"
      end
      end