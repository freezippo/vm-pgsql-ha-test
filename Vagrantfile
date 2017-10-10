Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.define :db1 do | m |
    m.vm.hostname = "db1"
    m.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end
    m.vm.network :private_network, ip: "192.168.33.11"
    m.vm.provision "shell", path: "setup.sh",
                   args: [1, "db1", "192.168.33.11", "db2", "192.168.33.12"]
  end
  config.vm.define :db2 do | m |
    m.vm.hostname = "db2"
    m.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end
    m.vm.network :private_network, ip: "192.168.33.12"
    m.vm.provision "shell", path: "setup.sh",
                   args: [2, "db2", "192.168.33.12", "db1", "192.168.33.11"]
  end
  config.vm.define :client do | m |
    m.vm.hostname = "client"
    m.vm.network :private_network, ip: "192.168.33.20"
    m.vm.provision "shell", path: "setup-client.sh"
  end
end
