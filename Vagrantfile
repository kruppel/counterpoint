# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.define 'counterpoint' do |box|
    box.vm.box = 'ubuntu/trusty64'
    box.vm.synced_folder '.', '/counterpoint'
    box.vm.network :'private_network', type:'dhcp', ip: '192.168.23.32'
    config.ssh.forward_agent = true
    box.vm.hostname='counterpoint'
    box.vm.provider 'virtualbox' do |v|
      v.name ='counterpoint'
      v.memory=8192
      v.cpus=4
    end
    box.vm.provision :shell, keep_color: true, inline: <<-SHELL
      sudo apt-get update

      sudo apt-get install -y openjdk-7-jdk
      sudo apt-get install -y autoconf libtool
      sudo apt-get -y install build-essential python-dev python-boto \
        libcurl4-nss-dev libsasl2-dev maven libapr1-dev libsvn-dev
      sudo apt-get install -y git
    SHELL
  end
end
