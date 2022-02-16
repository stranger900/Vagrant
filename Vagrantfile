Vagrant.configure("2") do |config|
	config.vm.define "server-ubuntu" do |web|
		web.vm.box = "ubuntu/focal64"
		web.vm.network "forwarded_port", id: "ssh", host: 2223, guest: 22
		web.vm.network "forwarded_port", id: "http", host: 8080, guest: 80
		web.vm.network "forwarded_port", id: "https", host: 8443, guest: 443
		web.vm.network "private_network", ip: "192.168.10.10", virtualbox__intnet: true
		web.vm.hostname = "server-ubuntu"
		web.vm.provision "shell", path: "provision.sh"			

		web.vm.provider "virtualbox" do |v|
      v.name = "server-ubuntu"
			v.memory = 1024
			v.cpus = 1
		end
	end

  config.vm.define "server-centos" do |web|
		web.vm.box = "geerlingguy/centos7"
		web.vm.network "forwarded_port", id: "ssh", host: 2224, guest: 22
		web.vm.network "private_network", ip: "192.168.10.20", virtualbox__intnet: true
		web.vm.hostname = "server-centos"			

		web.vm.provider "virtualbox" do |v|
      v.name = "server-centos"
			v.memory = 1024
			v.cpus = 1
		end
	end
end
