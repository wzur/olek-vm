# -*- mode: ruby -*-
# vi: set ft=ruby :

# I probably wouldn't change this
ip_address = "172.22.22.125"

# The project name is base for directories, hostname and alike
project_name = "olek"

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "wzurowski/centos7"

##     config.vm.network :forwarded_port, guest: 80, host: 8080

#    config.vm.synced_folder "./ztag" , "/var/www/" + project_name + "/", :mount_options => ["dmode=777", "fmode=666"]

    # Use hostonly network with a static IP Address and enable
    # hostmanager so we can have a custom domain for the server
    # by modifying the host machines hosts file
    config.hostmanager.enabled = true
    config.hostmanager.manage_host = true
    config.vm.define project_name do |node|
        node.vm.hostname = project_name + ".local"
        node.vm.network :private_network, ip: ip_address
        # enable audio drivers on VM settings
        node.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id,
            '--audio', 'pulse',
            '--audiocontroller', 'ac97',  # choices: hda sb16 ac97
            '--vram', '128',
            '--accelerate3d', 'on',
            '--clipboard', 'bidirectional',
            '--draganddrop', 'bidirectional'
            ]
          vb.name = 'Olek'
          vb.memory = 2048
        end

    end
    config.vm.provision :hostmanager

#    config.vm.provision :shell, :inline => "apt-get install -y python-minimal"
    config.vm.provision :ansible, :playbook => "./provisioning/site.yml"

end
