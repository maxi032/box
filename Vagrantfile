# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Base Box
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  # Connect to IP
  config.vm.network :private_network, ip: "192.168.5.0"

  # optional power Options (Remove if desired)
  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--memory", "500"]
    v.customize ["modifyvm", :id, "--cpus", "2"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  # Provisioning Script
  config.vm.provision "shell", path: "init.sh"

  # Synced Folder
  config.vm.synced_folder ".", "/vagrant/", :mount_options => [ "dmode=777", "fmode=666" ]
  config.vm.synced_folder "./www", "/vagrant/www/", :mount_options => [ "dmode=775", "fmode=644" ], :owner => 'vagrant', :group => 'www-data'

end
