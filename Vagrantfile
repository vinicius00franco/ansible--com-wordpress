Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  #config.ssh.private_key_path = "chave privada"
  #config.ssh.host = "172.17.177.40"
  #config.ssh.port = 22

  config.vm.define "wordpress" do |m|
	   m.vm.network "private_network", ip: "192.168.63.1"
	   m.vm.network "forwarded_port", guest: 80, host: 8080

     m.vm.provision "shell", inline: "cp /vagrant/id_wordpress.pub ."
     m.vm.provision "shell", inline: "cat id_wordpress.pub >> .ssh/authorized_keys"
  end

  config.vm.define "mysql" do |m|
    m.vm.network "private_network", ip: "192.168.63.10"
    m.vm.provision "shell", inline: "cp /vagrant/id_mysql.pub ."
    m.vm.provision "shell", inline: "cat id_mysql.pub >> .ssh/authorized_keys"
  end

  config.vm.provider "virtualbox" do |v|
	   v.memory = 1024
  end
end
