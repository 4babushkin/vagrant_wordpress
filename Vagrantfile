Vagrant.configure("2") do |config|

  config.vm.provider :virtualbox do |v|
    v.memory = 512
  end

  config.vm.define "dbserver" do |db|
    db.vm.box = "ubuntu/bionic64"
    db.vm.hostname = "dbserver"
    db.vm.network :private_network, ip: "10.10.10.10"

    db.vm.provision "ansible" do |ansible|
      ansible.playbook = "site.yml"
      ansible.groups = {
      "db" => ["dbserver"]
      }
    end

  end
  
  config.vm.define "appserver" do |app|
    app.vm.box = "ubuntu/bionic64"
    app.vm.hostname = "appserver"
    app.vm.network :private_network, ip: "10.10.10.20"

    app.vm.provision "ansible" do |ansible|
      ansible.playbook = "site.yml"
      ansible.groups = {
      "appserver" => ["appserver"],
      "appserver:vars" => { "db_host" => "10.10.10.10"}
      }

    end

  end
end