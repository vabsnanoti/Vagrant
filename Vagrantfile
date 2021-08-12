# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

$script = <<ENDSCRIPT
  sudo yum install -y epel-release
  sudo yum -y update
  sudo yum install -y net-tools
  sudo yum install -y wget
  sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo
   sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
  sudo yum install -y jenkins
  sudo yum install -y java-1.8.0-openjdk.x86_64
  sudo systemctl start jenkins.service
  sudo systemctl enable jenkins.service
ENDSCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos/7"
  config.vm.network "forwarded_port", guest: 8080, host: 8888
  config.vm.provision "shell", inline: $script
  config.vm.hostname = "myhost"
  config.vm.network "public_network", ip: "192.168.0.1", hostname: true
  config.vm.network "public_network", ip: "192.168.0.2"
end
