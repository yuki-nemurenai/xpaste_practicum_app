Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  config.vm.provision "file", source: "keys/rsa_key.pub", destination: "/home/vagrant/.ssh/"

  config.vm.define "controlnode" do |controlnode|
    controlnode.vm.box = "ubuntu/focal64"
    controlnode.vm.hostname = "controlnode"
    controlnode.vm.network "private_network", ip: "172.30.90.1"
    controlnode.vm.synced_folder "ansible","/home/vagrant/ansible"
    controlnode.vm.provision "file", source: "keys/rsa_key", destination: "/home/vagrant/.ssh/"
    controlnode.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/#g' /etc/ssh/sshd_config
      service ssh restart
      sudo apt update && sudo apt --assume-yes install ansible
      chmod 600 /home/vagrant/.ssh/rsa_key
      chmod 644 /home/vagrant/.ssh/rsa_key.pub
    SHELL
  end

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.define "centosnode" do |centosnode|
    centosnode.vm.box = "bento/centos-7.9"
    centosnode.vm.hostname = "centosnodenode"
    centosnode.vbguest.auto_update = false
    centosnode.vm.network "private_network", ip: "172.30.90.2"
    centosnode.vm.provision "shell", inline: <<-SHELL
      cat /home/vagrant/.ssh/rsa_key.pub >> /home/vagrant/.ssh/authorized_keys
    SHELL
  end
  config.vm.provider :virtualbox do |vb|  
    vb.customize ["modifyvm", :id, "--cpus", 2]
    vb.customize ["modifyvm", :id, "--memory", 2048]
  end

end