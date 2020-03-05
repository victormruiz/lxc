$script = <<-'SCRIPT'
sudo apt install python -y
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.define "mariadb" do |node|
    node.vm.provision "shell", inline: $script
    node.vm.network "private_network", ip: "192.168.122.2", lxc__bridge_name: 'virbr0'
    node.vm.box= "isc/lxc-ubuntu-19.04"
    node.vm.provider :lxc do |lxc|
      lxc.container_name = :machine # Sets the container name to 'db'
      lxc.container_name = 'mariadb'  # Sets the container name to 'mysql'
    end
  end

  config.vm.define "apache" do |node2|
    node2.vm.provision "shell", inline: $script
    node2.vm.network "private_network", ip: "192.168.122.3", lxc__bridge_name: 'virbr0'
    node2.vm.box= "isc/lxc-ubuntu-19.04"
    node2.vm.provider :lxc do |lxc|
      lxc.container_name = :machine # Sets the container name to 'db'
      lxc.container_name = 'apache'  # Sets the container name to 'mysql'
    end

end
end
