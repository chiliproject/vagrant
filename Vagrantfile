# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "lucid32"
  config.vm.box_url = "http://files.vagrantup.com/lucid32.box"

  # The box will only be available locally on this IP
  config.vm.network :hostonly, "10.0.43.42"

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks"]

    chef.data_bags_path = ["data_bags"]

    chef.add_recipe "apt"
    chef.add_recipe "postgresql::server"
    chef.add_recipe "chiliproject"
    chef.add_recipe "chiliproject::apache2"

    chef.json = {
      "postgresql" => {
        "password" => {
          "postgres" => "supersecretpostgressuperuserpassword"
        }
      }
    }
  end
end
