Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end
  
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Configuración de Ansible para la provisión local
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "/vagrant/playbook.yml"
  end

  # Provisión mediante shell para instalar software necesario
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update -y
    sudo apt-get install -y software-properties-common
    sudo apt-get update -y
    sudo apt-get install -y ansible
  SHELL
end