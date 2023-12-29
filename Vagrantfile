# -*- mode: ruby -*-
# vi: set ft=ruby :
NUM_MASTER_NODE = 1
NUM_WORKER_NODE = 2

#IP_NW = "192.168.0."

IP_NW = "192.168.0."
MASTER_IP_START = 80
NODE_IP_START = 81
LB_IP_START = 30


Vagrant.configure("2") do |config|
  config.vm.box = "generic/centos8"
  config.vm.box_version = "4.3.8"
  config.vm.box_check_update = false
  
  #Provision master node
  (1.. NUM_MASTER_NODE).each do |i|
    config.vm.define "icmp-master0#{i}" do |node|
      node.vm.provider "virtualbox" do |vb|
        vb.gui = false
        vb.name = "icmp-master0#{i}"
        vb.memory = "2048"
        vb.cpus = "2"
      end

      #Either this
      node.vm.hostname = "icmp-master0#{i}"
      node.vm.network :public_network, bridge: "en0: Wi-Fi", ip: IP_NW + "#{MASTER_IP_START + i}"

      #node.vm.network "forwarded_port", guest: 22, host: "#{2710 + i}"
      #Or Either this
      #ds.vm.hostname = "ds.iservermate.local"
      #ds.vm.network "public_network", bridge: "eno1", ip:"192.168.0.51"
      #config.vm.network "public_network"
      end

    config.vm.provision :ansible do |ansible|
      ansible.playbook = "SystemConfiguration.yml"
    end
  end
  
  #Provision worker node
  (1.. NUM_WORKER_NODE).each do |i|
    config.vm.define "icmp-worker0#{i}" do |node|
      node.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "icmp-node0#{i}"
      vb.memory = "2048"
      vb.cpus = "2"
    end

      #Either this
      node.vm.hostname = "icmp-worker0#{i}"
      node.vm.network :public_network, bridge: "en0: Wi-Fi", ip: IP_NW + "#{NODE_IP_START + i}"

      #node.vm.network "forwarded_port", guest: 22, host: "#{2711 + i}"
      #Or Either this
      #ds.vm.hostname = "ds.iservermate.local"
      #ds.vm.network "public_network", bridge: "eno1", ip:"192.168.0.51"
      #config.vm.network "public_network"
      end


    config.vm.provision :ansible do |ansible|
      ansible.playbook = "SystemConfiguration.yml"
    end
  end
end