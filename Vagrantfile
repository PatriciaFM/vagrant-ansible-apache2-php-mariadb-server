VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

    # SSH settings
    config.ssh.insert_key = true
    config.ssh.forward_agent = true

    # Box and bootstrap settings
    config.vm.box = "ubuntu/trusty64"
    config.vm.boot_timeout = 600
    config.vm.box_check_update = false

    # Network settings
    config.vm.network "private_network", ip: "192.168.33.33"

    # Forwarded port settings
    config.vm.network "forwarded_port", guest: 22, host: 2222, id: 'ssh'
    # config.vm.network "forwarded_port", guest: 80, host: 8080

    # Sync folder settings
    config.vm.synced_folder ".", "/var/www/local.example.com",
        id: "vagrant-root",
        owner: "vagrant",
        group: "www-data",
        mount_options: ["dmode=777,fmode=777"]

    # Virtual machine provider settings
    config.vm.provider "virtualbox" do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = false

      # Customize the amount of memory on the VM:
      vb.memory = "2048"
    end

    # Provisioning settings
    config.vm.provision "ansible" do |ansible|
        ansible.inventory_path = "./ansible/hosts"
        ansible.playbook       = "./ansible/playbooks/example.yml"
        ansible.limit          = "all"
        ansible.verbose        = "false"
    end

end
