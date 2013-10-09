# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  config.vm.forward_port 8000, 8000
  config.vm.forward_port 8080, 8080
  
  config.vm.network :hostonly, "10.80.80.80"
  config.vm.share_folder("vagrant-root", "/vagrant", "~/Sites", :nfs => true)
  
  config.ssh.forward_agent = true
  
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.add_recipe "apt"
    chef.add_recipe "build-essential"
    chef.add_recipe "git"
    chef.add_recipe "vim"
    chef.add_recipe "python"
    chef.add_recipe "nodejs::install_from_package"
    chef.add_recipe "gunicorn"
    chef.add_recipe "postgresql"
    chef.add_recipe "redisio::install"
    chef.add_recipe "redisio::enable"
    chef.add_recipe "xslt"
  end
  
  config.vm.provision :shell, :path => "setup.sh"
end
