Vagrant.configure("2") do |config|
  # Configuration de la machine virtuelle ansible-config
  config.vm.define "ansible-config" do |ansibleconfig|
    ansibleconfig.vm.box = "bento/ubuntu-22.04"
    #Configurer l'adresse IP de la machine virtuelle
    ansibleconfig.vm.network "private_network", ip: "192.168.33.13"
    ansibleconfig.vm.hostname = "ansible-config"
    # Configuration du fournisseur VirtualBox
    ansibleconfig.vm.provider "virtualbox" do |domain|
      domain.gui = false
      domain.name = "ansible-config"
      domain.cpus = 1
      domain.memory = 1024
    end 
  end
 
  # Configuration de la machine virtuelle ansible-client-db
  config.vm.define "ansible-client-db" do |ansibleclientdb|
    ansibleclientdb.vm.box = "bento/ubuntu-22.04"
    #Configurer l'adresse IP de la machine virtuelle
    ansibleclientdb.vm.network "private_network", ip: "192.168.33.14"
    ansibleclientdb.vm.hostname = "ansible-client-db"
    # Configuration du fournisseur VirtualBox
    ansibleclientdb.vm.provider "virtualbox" do |domain|
      domain.gui = false
      domain.name = "ansible-client-db"
      domain.cpus = 1
      domain.memory = 1024
    end
  end
  # Configuration de la machine virtuelle ansible-client-web
  config.vm.define "ansible-client-web" do |ansibleclientweb|
    ansibleclientweb.vm.box = "bento/ubuntu-22.04"
    #Configurer l'adresse IP de la machine virtuelle
    ansibleclientweb.vm.network "private_network", ip: "192.168.33.15"
    ansibleclientweb.vm.hostname = "ansible-client-web"
    # Configuration du fournisseur VirtualBox
    ansibleclientweb.vm.provider "virtualbox" do |domain|
      domain.gui = false
      domain.name = "ansible-client-web"
      domain.cpus = 1
      domain.memory = 1024
    end
  end 
end