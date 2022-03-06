# -*- mode: ruby -*-
# vi: set ft=ruby :
  
Vagrant.configure("2") do |config|
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"

  config.vm.define "nginx" do |nginx|
    nginx.vm.box = "ubuntu/bionic64"
    nginx.vm.box_check_update = false
    nginx.vm.network "forwarded_port", guest: 80, host: 8080
  end

  config.vm.define "jenkins" do |jenkins|
    jenkins.vm.box = "ubuntu/bionic64"
    jenkins.vm.box_check_update = false
    jenkins.vm.network "forwarded_port", guest: 8080, host: 8081
  end

  config.vm.provider 'virtualbox' do |vb|
    vb.memory = "512"
    vb.customize ['modifyvm', :id, '--cableconnected1', 'on']
  end
end
end