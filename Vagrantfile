# -*- mode: ruby -*-
# vi: set ft=ruby :

ipythonPort = 8001                 # Ipython port to forward (also set in IPython notebook config)

Vagrant.configure(2) do |config|
  config.ssh.insert_key = true
  config.vm.define "sparkvm" do |master|
    master.vm.box = "sparkmooc/base"
    master.vm.box_download_insecure = true
    master.vm.boot_timeout = 900
    master.vm.network :forwarded_port, host: ipythonPort, guest: ipythonPort, auto_correct: true   # IPython port (set in notebook config)
    master.vm.network :forwarded_port, host: 4040, guest: 4040, auto_correct: true                 # Spark UI (Driver)
    master.vm.hostname = "sparkvm"
    master.vm.usable_port_range = 4040..4090
    config.vm.synced_folder "src","/home/vagrant/labFiles"
    config.ssh.private_key_path = "~/.ssh/id_rsa"
    config.vm.provider :digital_ocean do |provider|
    	provider.client_id = "22376b44b841d2528e9aceeab1260c90"
    	provider.api_key = "babb788559e9ce1d4939feee9ae96d77"
    	provider.image = "Ubuntu 12.10 x64"
    	provider.region = "New York 2"
    end
  end
end
