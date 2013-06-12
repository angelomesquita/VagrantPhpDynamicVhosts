# -*- mode: ruby -*-
# vi: set ft=ruby :

  Vagrant.configure("2") do |config|

  config.vm.box = "php54"

  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  config.vm.network :forwarded_port, guest: 80, host: 8080
 
 config.vm.network :forwarded_port, guest: 3306, host: 3333
 
  config.vm.network :public_network

  config.vm.provision :puppet do |puppet|
            puppet.manifests_path = "puppet/manifests"
            puppet.manifest_file  = "base.pp"
            puppet.module_path = "puppet/modules"
            # puppet.options = "--verbose --debug"
            # puppet.options = "--verbose"
  end

end
