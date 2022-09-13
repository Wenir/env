# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # https://docs.vagrantup.com.

  config.vm.box = "tranphuquy19/ubuntu-22.04-desktop"
  # config.vm.synced_folder "fs/", "/sync"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.

  config.vm.network "private_network", ip: "192.168.56.11"

  # config.ssh.private_key_path = "~/.ssh/id_ed25519"
  config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.gui = true
    vb.memory = "2048"
    vb.customize ["modifyvm", :id, "--graphicscontroller", "vmsvga"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "main.yml"
    ansible.verbose = true
  end

  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
