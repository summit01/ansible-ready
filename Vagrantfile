VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/id_rsa.pub"

  config.vm.define "vagrant1" do |vagrant1|
    vagrant1.vm.box = "ubuntu/trusty64"
    vagrant1.vm.network "private_network", ip: "192.168.33.10"
    vagrant1.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    end
  end
  config.vm.define "vagrant2" do |vagrant2|
    vagrant2.vm.box = "centos/7"
    vagrant2.vm.network "private_network", ip: "192.168.33.20"
    vagrant2.vm.network "forwarded_port", guest: 8080, host: 80
    vagrant2.vm.network "forwarded_port", guest: 443, host: 8443
    vagrant2.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    end
  end

  config.vm.define "vagrant3" do |vagrant3|
    vagrant3.vm.box = "bento/centos-7.2"
    vagrant3.vm.network "private_network", ip: "192.168.33.30"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end
    vagrant3.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    end
  end
end