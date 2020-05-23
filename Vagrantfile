$useraddscript = <<SCRIPT
useradd -m henk
groupadd operators
usermod -aG operators henk
mkdir /operators
chown henk /operators
chgrp operators /operators
SCRIPT


Vagrant.configure('2') do |config|
    
    # set default settings
	config.ssh.insert_key = false
    config.vm.box = "ubuntu/bionic64"
    config.vm.provider "virtualbox" do |vb|
        vb.memory = 1024
        vb.cpus = 2
    end

    config.vm.define "master", primary: true do |machine1|
        machine1.vm.host_name = "master.local"
        machine1.vm.network "private_network", ip: "192.168.10.160"
        machine1.vm.provision "shell", inline: $useraddscript
		machine1.vm.provision :shell, :inline => "sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config; sudo systemctl restart sshd;", run: "always"
        machine1.vm.provision "ansible" do |ansible|
			ansible.playbook = "initial.yaml"
			ansible.playbook = "master.yaml"
			ansible.extra_vars = {
                node_ip: "192.168.10.160",
            }
        end
    end

    config.vm.define "worker1", primary: false do |machine2|
        machine2.vm.host_name = "worker1.local"
        machine2.vm.network "private_network", ip: "192.168.10.161"
        machine2.vm.provision "shell", inline: $useraddscript
		machine2.vm.provision :shell, :inline => "sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config; sudo systemctl restart sshd;", run: "always"
        machine2.vm.provision "ansible" do |ansible|
			ansible.playbook = "initial.yaml"
			ansible.playbook = "worker.yaml"
			ansible.extra_vars = {
                node_ip: "192.168.10.161",
            }
        end
    end
	    config.vm.define "worker2", primary: false do |machine3|
        machine3.vm.host_name = "worker2.local"
        machine3.vm.network "private_network", ip: "192.168.10.162"
        machine3.vm.provision "shell", inline: $useraddscript
		machine3.vm.provision :shell, :inline => "sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config; sudo systemctl restart sshd;", run: "always"
        machine3.vm.provision "ansible" do |ansible|
			ansible.playbook = "initial.yaml"
			ansible.playbook = "worker.yaml"
			ansible.extra_vars = {
                node_ip: "192.168.10.162",
            }
        end
    end
end