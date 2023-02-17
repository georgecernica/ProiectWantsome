Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  config.vm.network "private_network", ip: "192.168.56.17"
  config.vm.network "public_network"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "6133"
    vb.cpus = "3"
  end
end  