Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "private_network", ip: "192.168.56.17"
  config.vm.network "public_network"
  config.vm.synced_folder "./", "/var/wantsome"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "6144"
    vb.cpus = "3"
  end 
  
    
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    sudo apt-get update
    sudo apt-get install -y docker-ce
    sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    sudo usermod -aG docker vagrant
    sudo chown vagrant /var/run/docker.sock
    sudo chown vagrant:docker /var/run/docker.sock && sudo chmod g+rwx /var/run/docker.sock

  
  SHELL
end  