# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "sdn" do |sdn|
    sdn.vm.box = "ubuntu/trusty64"
    sdn.vm.network :private_network, ip: "192.168.33.20"
    # NOTE(ahill): Uncomment if you want to sync folders between your local machine and this VM
    # sdn.vm.synced_folder "src/", "/home/vagrant/sdn/src"
    sdn.vm.provision "ansible" do |ansible| 
      ansible.extra_vars = { ansible_ssh_user: 'vagrant' 
      # NOTE(ahill): to install a specific version just pass the git tag. e.g.:
      # ovs_version = 'v2.3.1'
      # mininet_version = '2.2.0'
      # ryu_version = 'v3.1.6'
      }
      ansible.playbook = "sdn.yaml"
    end
  end

  # NOTE(ahill): Uncomment this if you wish to use 'xterm' functionality in mininet
  # config.ssh.forward_x11 = true

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "1024"]
  end
end