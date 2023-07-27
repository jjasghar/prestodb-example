# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # General Vagrant VM configureation
  config.vm.box = "boxomatic/centos-stream-9"
  config.ssh.insert_key = false
  config.vm.synced_folder ".","/vagrant", disabled: true

  config.vm.provider :virtualbox do |v|
    v.memory = 4046
    v.linked_clone = true
  end

  # prestodb server
  config.vm.define "presto" do |app|
    app.vm.hostname = "presto.example.com"
    app.vm.network :private_network, ip: "192.168.56.4"
    app.vm.network "forwarded_port", guest: 8080, host: 8080

    app.vm.provision :ansible do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "playbooks/presto.yml"
    end
  end

  # mariadb server
  config.vm.define "mariadb" do |app|
    app.vm.hostname = "mariadb.example.com"
    app.vm.network :private_network, ip: "192.168.56.6"

    app.vm.provision :ansible do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "playbooks/mariadb.yml"
    end
  end

  # redis server
  config.vm.define "redis" do |app|
    app.vm.hostname = "redis.example.com"
    app.vm.network :private_network, ip: "192.168.56.5"

    app.vm.provision :ansible do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "playbooks/redis.yml"
    end
  end

end
