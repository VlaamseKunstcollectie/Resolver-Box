# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/jessie64"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.synced_folder "/Users/matthiasvandermaesen/Workspace/resolver", "/vagrant", type: "nfs"

  config.vm.define "virtualbox" do |virtualbox|
    virtualbox.vm.hostname = "resolver-dev-box"
    virtualbox.vm.network "private_network", ip: "192.168.2.158"
    virtualbox.ssh.forward_agent = true

    config.vm.provider :virtualbox do |v|
      v.name = "Resolver development box"
      v.customize [
        "modifyvm", :id,
        "--name", "resolvers-dev-box",
        "--memory", 4096,
        "--cpus", 1,
      ]
    end
  end

end
