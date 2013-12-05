# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.ssh.username = "vagrant"
  config.ssh.private_key_path = File.expand_path("~/.vagrant.d/insecure_private_key")
  # config.vm.network :public_network
  # config.ssh.forward_agent = true
  
  config.vm.provider :virtualbox do |virtualbox|
    virtualbox.customize ["modifyvm", :id, "--memory", 512]
  end

  config.vm.define :app do |node|
    node.vm.box = "cent6_64_min"
    node.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v0.1.0/centos64-x86_64-20131030.box"
    node.vm.hostname = "app.dev"
    node.vm.network :forwarded_port, guest: 80, host: 8081
    node.vm.network :private_network, ip: "192.168.100.222"
  end

  config.vm.define :front do |node|
    node.vm.box = "cent6_64_min"
    node.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v0.1.0/centos64-x86_64-20131030.box"
    node.vm.hostname = "front.dev"
    node.vm.network :forwarded_port, guest: 80, host: 8080
    node.vm.network :private_network, ip: "192.168.100.111"
    node.vm.provision :ansible do |ansible|
      ansible.playbook = "provisioning/site.yml"
      ansible.host_key_checking = "false"
      ansible.inventory_file = "hosts"
      ansible.verbose = "vvvv"
    end
  end
  
end