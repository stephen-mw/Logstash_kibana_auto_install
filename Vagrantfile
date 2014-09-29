# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.provision :shell, :path => "logstash_server"

  # Give it a little more memory than default
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
  end

  # Forward local port 8080 to guest port 80
  config.vm.network "forwarded_port", guest: 80, host: 8080

end
