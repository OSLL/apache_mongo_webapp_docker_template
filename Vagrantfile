# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.provider "docker" do |d|

    d.has_ssh = true
    d.image = "apache_mongo_webapp_docker_template:v1"

    config.vm.provision "shell", inline: <<-EOC
      sudo /etc/init.d/apache2 start
      sudo LC_ALL="en_US.UTF-8" /etc/init.d/mongodb start
    EOC
   
  end
end
