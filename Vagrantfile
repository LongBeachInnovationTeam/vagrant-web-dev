# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Configure proxy for the City's internal proxy
  if Vagrant.has_plugin?("vagrant-proxyconf")
    config.proxy.http     = "http://alchave:!4en3msa@proxy1.ci.long-beach.ca.us:80/"
    config.proxy.https    = "http://alchave:!4en3msa@proxy1.ci.long-beach.ca.us:80/"
    config.proxy.no_proxy = "localhost,127.0.0.1"
    config.apt_proxy.http = "http://alchave:!4en3msa@proxy1.ci.long-beach.ca.us:80/"
    config.apt_proxy.https = "DIRECT"
  end

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 80, host: 8080     # Standard web port
  config.vm.network "forwarded_port", guest: 3000, host: 3000   # Meteor default
  config.vm.network "forwarded_port", guest: 27017, host: 27017 # MongoDB default
  config.vm.network "forwarded_port", guest: 5432, host: 5432   # PostgreSQL default

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "C://Users//alchave//Projects", "/home/vagrant/Projects"

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y curl g++ git htop python-pip
    sudo pip install django
    mkdir /home/vagrant/Downloads
    wget http://nodejs.org/dist/latest/node-v0.12.4-linux-x64.tar.gz -P /home/vagrant/Downloads
    sudo tar -C /usr/local --strip-components 1 -xzf /home/vagrant/Downloads/node-v0.12.4-linux-x64.tar.gz
    ls -l /usr/local/bin/node
    ls -l /usr/local/bin/npm
    sudo npm install -g bower yo
    sudo apt-get install -y golang
    sudo curl https://install.meteor.com/ | sh
    sudo apt-get install -y postgresql postgresql-contrib
    sudo apt-get install -y mongodb
    sudo pip install cubes[all] flask sqlalchemy
  SHELL
end
