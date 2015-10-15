# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

module OS
    def OS.windows?
        (/cygwin|mswin|mingw|bccwin|wince|emx/ =~ RUBY_PLATFORM) != nil
    end

    def OS.mac?
        (/darwin/ =~ RUBY_PLATFORM) != nil
    end

    def OS.unix?
        !OS.windows?
    end

    def OS.linux?
        OS.unix? and not OS.mac?
    end
end

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
#  config.vm.box_url = "http://files.vagrantup.com/trusty64.box"

  config.vm.network "private_network", ip: "192.168.192.168"
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id,  "--memory", "1024", "--cpus", "2"]
  end

  if OS.windows?
    config.vm.synced_folder ".", "/vagrant", type: "smb"
  elsif OS.unix?
    config.vm.synced_folder ".", "/vagrant", type: "nfs"
  end

  # Shared folder from the host machine to the guest machine. Uncomment the line
  # below to enable it.
  #config.vm.synced_folder "../../../my-cool-app", "/webapps/mycoolapp/my-cool-app"
  config.ssh.forward_agent = true

  ## Ansible provisioner.
  #config.vm.provision "ansible" do |ansible|
    #ansible.playbook = "vagrant.yml"
    #ansible.host_key_checking = false
    #ansible.verbose = "vvvv"
  #end
end
