# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "geerlingguy/centos7"
  config.vm.box_url = "https://atlas.hashicorp.com/geerlingguy/boxes/centos7"

  # synced fonder
  config.vm.synced_folder ".", "/vagrant", :mount_options => ['dmode=775', 'fmode=664']

  # port forwardsu
  config.vm.network :forwarded_port, guest: 80, host: 80        # nginx
  config.vm.network :forwarded_port, guest: 5432, host: 5432    # PostgreSQL
  config.vm.network :forwarded_port, guest: 6379, host: 6379    # Redis

  # Enable Provisioning
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provisioning/provisioning.yml"
    ansible.limit = "all"
    ansible.inventory_path = "provisioning/hosts"
  end
end
