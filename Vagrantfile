# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	config.vm.box_download_insecure=true
  config.vm.provision :shell, path: "pg_config.sh"
  config.vm.box = "bento/ubuntu-16.04-i386"
  config.vm.network "forwarded_port", guest: 5000, host: 5000
  config.vm.network "forwarded_port", guest: 8008, host: 8008, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 8088, host: 8088, host_ip: "127.0.0.1"
  if Vagrant.has_plugin?("vagrant-proxyconf")
    config.proxy.http     = "http://3.28.29.241:88/"
    config.proxy.https    = "https://3.28.29.241:88/"
    config.proxy.no_proxy = "localhost,127.0.0.1,.example.com"
  end
  # Work around disconnected virtual network cable.
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
  end
end
