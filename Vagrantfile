# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "lucid32"
  config.vm.box_url = "http://files.vagrantup.com/lucid32.box"

  # The default ChiliProject  will be available on http://localhost:4223
  # CAUTION: if you change this, you must remember to change the port of the
  #          external_uri parameter in data_bags/chiliproject/default.json
  config.vm.forward_port 80, 4223

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks"]

    chef.data_bags_path = ["data_bags"]

    chef.add_recipe "apt"
    chef.add_recipe "postgresql::server"
    chef.add_recipe "chiliproject"
    chef.add_recipe "chiliproject::apache2"

    chef.json = {
      "chiliproject" => {
        "apache" => {
          "serve_aliases" => true
        }
      },
      "postgresql" => {
        "password" => {
          "postgres" => "supersecretpostgressuperuserpassword"
        }
      }
    }
  end
end
