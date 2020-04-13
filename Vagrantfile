# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "bento/ubuntu-16.04"
  config.vm.provider "hyperv" do |hyperv|
    hyperv.cpus = "2"
    hyperv.enable_virtualization_extensions = true
    hyperv.memory = "3072"
  end
  # config.vm.provision "shell", inline: "yum install -y httpd"
  
  config.vm.define "masternode1" do |masternode1|
    masternode1.vm.hostname = "masternode1"
  end

  config.vm.define "workernode1" do |workernode1|
    workernode1.vm.hostname = "workernode1"
    # workernode1.vm.provision "shell", inline: "sudo apt update; sudo apt install mysql -y"
  end

  config.vm.define "workernode2" do |workernode2|
    workernode2.vm.hostname = "workernode2"
  end

  # config.vm.network = "public_network"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "vmware_desktop" do |v|
    # Display the vmware GUI when booting the machine
    v.gui = false
    # Customize the amount of memory on the VM:
    v.vmx["numvcpus"] = "2"
    v.vmx["memsize"] = "3072"
  end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get upgrade -y
  # SHELL
  # end

  config.vm.provision "shell" do |s|
    ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
    s.inline = <<-SHELL
      echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
      export DEBIAN_FRONTEND=noninteractive
      apt-get update
      apt-get upgrade -qy
    SHELL
  end

end