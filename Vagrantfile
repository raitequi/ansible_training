Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provider "virtualbox" do |v|
   v.memory = 512
   v.cpus = 1
 end

  config.vm.define "wordpress" do |wordpress|
     wordpress.vm.network "public_network", ip: "192.168.15.241", bridge: 'wlp2s0'
     wordpress.vm.provision "shell",
      inline: "chmod 700 .ssh && chmod 600 .ssh/authorized_keys && \
      cat /vagrant/id_rsa.pub >> .ssh/authorized_keys && hostname -I"
     wordpress.vm.provision "ansible" do |ansible|
       ansible.playbook = "/home/asuspc/vagrant_teste/bionic/maquina_ansible/playbook.yml"
     end
   end

  config.vm.define "mysqlserver" do |mysqlserver|
     mysqlserver.vm.network "public_network", ip: "192.168.15.242", bridge: 'wlp2s0'
     mysqlserver.vm.provision "shell",
      inline: "chmod 700 .ssh && chmod 600 .ssh/authorized_keys && \
      cat /vagrant/id_rsa.pub >> .ssh/authorized_keys && hostname -I"
     mysqlserver.vm.provision "ansible" do |ansible|
      ansible.playbook = "/home/asuspc/vagrant_teste/bionic/maquina_ansible/playbook.yml"
     end
    end
  end
