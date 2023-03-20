# -*- mode: ruby -*-
# vi: set ft=ruby :
# virsh pool-create-as --name data --type dir --target /mnt/data

Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2004"
  config.vm.define "scala_192.168.33.112"
  config.vm.network "private_network", ip: "192.168.33.112"
  config.vm.hostname = "scala"

  config.vm.provider "libvirt" do |kvm|
    kvm.memory = 4096 
    kvm.cpus = 2
    kvm.storage_pool_name = "data"
    kvm.machine_type = "q35"
  end

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
   sudo apt update
   sudo apt install software-properties-common
   sudo apt-add-repository --yes --update ppa:ansible/ansible
   sudo apt install -y ansible
   git clone https://github.com/developer-onizuka/ansible
   ansible-playbook ansible/google-chrome.yaml
   ansible-playbook ansible/scala.yaml
   ansible-playbook ansible/vscode.yaml
   ansible-playbook ansible/docker.yaml
   #sudo docker pull jupyter/all-spark-notebook:c1b0cf6bf4d6
   sudo docker pull jupyter/all-spark-notebook:spark-3.2.0
   SHELL
end
