# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "ubuntu-10.04.4-server-amd64"
  config.vm.network :hostonly, "192.168.56.10"
  # config.vm.network :bridged
  # config.vm.forward_port 80, 8080
  config.vm.share_folder "v-data", "/vagrant_data", "../data"
  # config.vm.provision :puppet do |puppet|
  #   puppet.manifests_path = "manifests"
  #   puppet.manifest_file  = "base.pp"
  # end

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "mysql"
    chef.add_role "web"
  
    # You may also specify custom JSON attributes:
    chef.json = { :mysql_password => "foo" }
  end
end
