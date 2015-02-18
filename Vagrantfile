# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "nfq/wheezy"
    config.vm.box_url = "https://vagrantcloud.com/nfq/boxes/wheezy/versions/1.1/providers/virtualbox.box"

    config.vm.network :private_network, ip: "192.168.111.222"

    config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end
end
