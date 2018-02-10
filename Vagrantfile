# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"

  # Mesos Mester
  (1..1).each do |i|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    config.vm.define "mesos-m0#{i}" do |master|
      master.vm.hostname = "mesos-m0#{i}"
      master.vm.network "private_network", ip: "10.0.0.1#{i}"
    end
  end

  # Mesos Slave
  (1..3).each do |i|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    config.vm.define "mesos-s0#{i}" do |slave|
      slave.vm.hostname = "mesos-s0#{i}"
      slave.vm.network "private_network", ip: "10.0.0.2#{i}"
    end
  end

  # Provision
  config.vm.provision "shell", path: "provision.sh"
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/authorized_keys"

end
