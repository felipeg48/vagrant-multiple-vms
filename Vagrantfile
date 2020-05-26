Vagrant.configure("2") do |config|

  config.vm.provision "file", source: "keys/.ssh/vagrant_id_rsa.pub", destination: "~/.ssh/authorized_keys"
  config.ssh.insert_key = false
  config.ssh.private_key_path = ["keys/.ssh/vagrant_id_rsa", "~/.vagrant.d/insecure_private_key"]


  config.vm.network "public_network", bridge: [
    "en0: Wi-Fi (Wireless)"
  ]

  config.vm.provider "virtualbox" do |vb|
      vb.linked_clone = true
      vb.memory = "1024"
      vb.cpus = 1
  end

  config.vm.define "controller" do |ctrl|
    ctrl.vm.hostname = "controller"
    ctrl.vm.box = "centos/8"
    ctrl.vm.box_version = "1905.1"
    ctrl.vm.box_check_update = false
    ctrl.vm.provision :shell, path: "scripts/install-ansible.sh"
  end

  config.vm.define "managed-node-1" do |mn1|
    mn1.vm.hostname = "managed-node-1"
    mn1.vm.box = "centos/8"
    mn1.vm.box_version = "1905.1"
    mn1.vm.box_check_update = false
    mn1.vm.provision :shell, path: "scripts/install-python.sh"
  end

  config.vm.define "managed-node-2" do |mn2|
    mn2.vm.hostname = "managed-node-2"
    mn2.vm.box = "centos/8"
    mn2.vm.box_version = "1905.1"
    mn2.vm.box_check_update = false
    mn2.vm.provision :shell, path: "scripts/install-python.sh"
  end

end
