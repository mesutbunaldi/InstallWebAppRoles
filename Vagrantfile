# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # Box
  config.vm.box = "ubuntu/bionic64"
  
  config.vm.box_version = "20220325.0.0"

  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # Provider & Specs
  config.vm.provider :virtualbox do |v|
    v.memory = 1024
    v.cpus = 1
  end

#   (1..4).each do |i|
# 		# Defining VM properties
# 		config.vm.define "nginx#{i}" do |node|
# 			# Specifying the provider as VirtualBox and naming the VM's
# 			node.vm.hostname = "nginx#{i}" 
#       node.vm.network :private_network, ip: "192.168.56.2#{i}"
# 		end
# 	end

  config.vm.define "turknet" do |machine|
    machine.vm.hostname = "turknet"
    machine.vm.network :private_network, ip: "192.168.56.21"
  end


  config.vm.provision "ansible" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.playbook = "playbook.yml"
    ansible.inventory_path = "inventory" # buraya public_key eklenmeli ki provisioner makine gidip remote makineye erişebilsin
    ansible.limit = "all"
    ansible.become = true
    ansible.verbose = "v"
    #ansible.config+file = 'ansible.cfg'
  end

end
