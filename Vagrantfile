Vagrant.configure("2") do |config|
    config.vm.define "ansible" do |ansible|
        ansible.vm.provider "virtualbox" do |v|
            v.gui = true
            v.name = "AnsibleControlMachineRH7"
            v.memory = 512
            v.cpus = 2
        end
        ansible.vm.box = "centos/7"
        
        # https://community.spiceworks.com/how_to/110616-install-ansible-on-64-bit-centos-6-6
        ansible.vm.provision "shell",
            inline: "echo cd ansible >> .bashrc; yum -y install epel-release; yum -y install wget git zip unzip ansible"

        # https://oddessay.com/development-notes/changing-vagrants-default-ssh-port-to-prevent-collision-when-resuming-a-suspended-instance
        ansible.vm.network "forwarded_port", guest: 22, host: 2220, id: "ssh"

        # Issue with synced folder on Windows: https://github.com/hashicorp/vagrant/issues/6769#issuecomment-252151694
        # Issue with ssh keys permission too open: https://stackoverflow.com/questions/35807568/vagrant-synced-folder-permissions
        # Issue with ssh keys permission too open: https://github.com/ansible/ansible/issues/42388#issuecomment-405950940
        ansible.vm.synced_folder "../", "/home/vagrant/ansible", disabled: false, mount_options: ["dmode=700,fmode=700"]
    end
end
