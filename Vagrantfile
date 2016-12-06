

## Configure virtual machine
## -------------------------

Vagrant.configure(2) do |config|
	config.vm.box = "centos/7"
	config.vm.box_version = "1610.01"
	config.vm.box_check_update = false
	config.ssh.forward_agent = true

	## Disable default shared folder (Shared folder can be configured later with virtualbox)
	config.vm.synced_folder ".", "/vagrant", disabled: true
	config.vm.synced_folder ".", "/home/vagrant/sync", disabled: true
	
	## Common virtual box settings
	config.vm.provider "virtualbox" do |vb|
		vb.gui = false
		vb.memory = "512"
		vb.cpus = 1
		#vb.linked_clone = true
	end
  
  
#	N = 3
#	(1..N).each do |machine_id|
#		config.vm.define "machine#{machine_id}" do |machine|
#			machine.vm.provider "virtualbox" do |v|
#				v.name = "machine#{machine_id}"
#			end
#			machine.vm.hostname = "machine#{machine_id}"
#			machine.vm.network "private_network", ip: "192.168.56.#{9+machine_id}"

			## Only execute once the Ansible provisioner,
			## when all the machines are up and ready.
			#if machine_id == N
			#	machine.vm.provision :ansible do |ansible|
			#		# Disable default limit to connect to all the machines
			#		ansible.limit = "all"
			#		ansible.playbook = "playbook.yml"
			#	end
			#end

#		end
#	end


	config.vm.define "node1" do |machine|
		machine.vm.provider "virtualbox" do |v|
			v.name = "node1"
		end
		machine.vm.hostname = "node1"
		machine.vm.network :private_network, ip: '192.168.56.11'
	end

	config.vm.define "node2" do |machine|
		machine.vm.provider "virtualbox" do |v|
			v.name = "node2"
		end
		machine.vm.hostname = "node2"
		machine.vm.network "private_network", ip: "192.168.56.12"
	end  

	config.vm.define "controller" do |machine|
		machine.vm.provider "virtualbox" do |v|
			v.name = "controller"
		end
		machine.vm.hostname = "controller"
		machine.vm.network "private_network", ip: "192.168.56.10"
	end  

	## Provisioning
	#config.vm.provision "shell", path: "provision_sw.sh"

	## Reboot at the end (e.g to disable SELinux)
	#config.vm.provision "shell", inline: "/sbin/reboot"
  
end
