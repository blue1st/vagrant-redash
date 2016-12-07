# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "geerlingguy/centos7"
  config.vm.box_url = "https://atlas.hashicorp.com/geerlingguy/boxes/centos7"
  config.vm.define "redash" do | m |
    m.vm.hostname = "redash"
    m.vm.network "private_network", ip: "192.168.33.200"
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbooks/site.yml"
    ansible.host_key_checking = false
    ansible.groups = {
      "redash" => ["redash"],
      "redis" => ["redash"],
      "postgresql" => ["redash"],
    }
  end
  config.ssh.forward_agent = true
end
