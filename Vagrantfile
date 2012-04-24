# -*- mode: ruby -*-
# vi: set ft=ruby :

address = "192.168.56.10"

Vagrant::Config.run do |config|
  config.vm.box = "ubuntu-10.04.4-server-amd64"
  config.vm.network :hostonly, "#{address}"
  # config.vm.network :bridged
  # config.vm.forward_port 80, 8080
  config.vm.share_folder "v-data", "/vagrant_data", "../data"
  # config.vm.provision :puppet do |puppet|
  #   puppet.manifests_path = "manifests"
  #   puppet.manifest_file  = "base.pp"
  # end

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "graphite"
    chef.json = {
      "graphite" => {
        "carbon" => {
          "line_receiver_interface" => "#{address}",
          "pickle_receiver_interface" => "#{address}",
          "cache_query_interface" => "#{address}"
        }
      }
    } 
  end
end
