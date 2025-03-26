Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-24.04"
  config.vm.box_version = "202502.21.0"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8186"
    vb.cpus = 2

    number_of_hdds = 5
    hdd_size = 5 * 1024  
    number_of_hdds.times do |i|
        vb.customize ["createhd", "--filename", "disk#{i + 1}.vdi", "--size", hdd_size]
        vb.customize ["storageattach", :id, "--storagectl", "SATA Controller", "--port", i + 1, "--device", 0, "--type", "hdd", "--medium", "disk#{i + 1}.vdi"]
    end
  end
end
