# Number of VM's to spawn
num_instances = 2

# VM Basename
instance_name_prefix="ubuntu-boxes"

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  # Settings for vagrant boxes

  # Set up each box
  (1..num_instances).each do |i|
    vm_name = "%s-%02d" % [instance_name_prefix, i]
    config.vm.define vm_name do |host|
      host.vm.hostname = vm_name

      # Create ip address and assign hostname
      ip = "172.10.10.#{i+100}"
      host.vm.network :private_network, ip: ip

      #Setup docker 
      host.vm.provision :docker
    end
  end

  #shell commands to setup pre installed apps
  config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install -y vim
   SHELL
end
