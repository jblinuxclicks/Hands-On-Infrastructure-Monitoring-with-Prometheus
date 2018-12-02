# -*- mode: ruby -*-
# vi: set ft=ruby :

GUI     = false
RAM     = 256
DOMAIN  = ".prom.inet"
NETWORK = "192.168.77."
NETMASK = "255.255.255.0"
BOX     = 'bento/ubuntu-18.04'

Vagrant.configure(2) do |config|

  if ENV['SETUP'] == 'chapter03'

    config.vm.define "prometheus" do |prometheus|
      prometheus.vm.box = BOX
      prometheus.vm.provider "virtualbox" do |vbox|
        vbox.gui    = GUI
        vbox.memory = RAM
        vbox.name = "prometheus"
      end
      prometheus.vm.hostname = "prometheus" + DOMAIN
      prometheus.vm.network 'private_network', ip: NETWORK + "10", netmask: NETMASK
      prometheus.vm.network "forwarded_port", guest: 9090, host: 9090
      prometheus.vm.provision "shell", path: "chapter03/provision/prometheus.sh"
    end
  end

end
