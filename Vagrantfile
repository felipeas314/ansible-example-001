Vagrant.configure("2") do |config|
  
  config.vm.box = "centos/8"
  config.vm.synced_folder".", "/vagrant", disabled: true
  
  config.vm.define "vm_jenkins" do |vm_jenkins|
    
    vm_jenkins.vm.network "forwarded_port", guest: 8080, host:9090, protocol: "tcp"
    # config.vm.network "private_network", ip: "192.168.50.4"
    vm_jenkins.vm.network "private_network", type: "dhcp"
    # config.vm.network "public_network"

    vm_jenkins.vm.provision "ansible" do |ansible|
      ansible.playbook = "main.yml"
    end
    
    vm_jenkins.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end

  end

end