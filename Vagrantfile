# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.define :centos_node do |nodeOne|
        nodeOne.vm.box = "centos64_updated4"
        nodeOne.vm.network :private_network, ip: "192.168.56.101"
        nodeOne.vm.network "public_network", :bridge => "eth4", ip:"192.168.131.1", :auto_config => "false", :netmask => "255.255.255.0"
        nodeOne.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", "1024","--cpus", "4", "--name", "centos_flask" ]
        end
    config.vm.provision :chef_solo do |chefOne|
				chefOne.cookbooks_path = "cookbooks"
				chefOne.add_recipe "flask"
				#chefOne.add_recipe "mirror"
				#chefOne.json = {"aptmirror" => {"server" => "192.168.131.254"}}
				end
    end

    config.vm.define :centos_database do |nodeTwo|
        nodeTwo.vm.box = "centos64_updated4"
        nodeTwo.vm.network :private_network, ip: "192.168.56.102"
        nodeTwo.vm.network "public_network", :bridge => "eth4", ip:"192.168.131.2", :auto_config => "false", :netmask => "255.255.255.0"
        nodeTwo.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", "1024","--cpus", "4", "--name", "centos_dbpost"]
        end
	config.vm.provision :chef_solo do |chefTwo|
		      	chefTwo.cookbooks_path = "cookbooks"
		      	#chefTwo.add_recipe "mirror"
		      	chefTwo.add_recipe "postgres"
		      	#chefTwo.json ={"aptmirror" => {"server" => "192.168.131.254"}}    
		      	end
	end

end
