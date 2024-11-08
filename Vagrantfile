Vagrant.configure("2") do |config|
  config.vm.define "nginx_server" do |nginx|
    nginx.vm.box = "ubuntu/focal64"

    nginx.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
    nginx.vm.network "private_network", ip: "192.168.33.10"

    nginx.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 4
    end

    nginx.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "/vagrant/playbook.yml"
    end

    nginx.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update -y
      sudo apt-get install -y software-properties-common
      sudo apt-get update -y
      sudo apt-get install -y ansible
    SHELL
  end
end