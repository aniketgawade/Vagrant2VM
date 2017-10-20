# Vagrant2VM
Vagrant file to spawn multiple connected VM's


To add to bridged network add :
config.vm.network "public_network", bridge: "br-mgmt"
