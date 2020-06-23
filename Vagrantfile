Vagrant.configure("2") do |config|
    config.vm.box = "local/hashistack"
    config.vm.network "private_network", ip: "10.0.3.10"

    # Hashicorp consul ui
    config.vm.network "forwarded_port", guest: 8500, host: 8500, host_ip: "127.0.0.1"
    # Hashicorp nomad ui
    config.vm.network "forwarded_port", guest: 4646, host: 4646, host_ip: "127.0.0.1"
    # Hashicorp vault ui
    config.vm.network "forwarded_port", guest: 8200, host: 8200, host_ip: "127.0.0.1"

    config.vm.provider "virtualbox" do |vb|
        vb.linked_clone = true
        vb.memory = 2048
    end
    config.vm.provision "ansible_local" do |startup|
        run = "always"
        startup.playbook = "/etc/ansible/startup.yml"
    end
end
