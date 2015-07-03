Vagrant::Config.run do |config|
  config.vm.box = "precise32"
  
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  config.vm.forward_port 22, 22
  
  config.vm.forward_port 3000, 3000
  
  config.vm.forward_port 27017, 27017

  config.vm.share_folder "app", "/home/vagrant/app", "app"
  
  config.vm.share_folder "app", "/home/vagrant/app", "app"

  # Uncomment the following line to allow for symlinks
  # in the app folder. This will not work on Windows, and will
  # not work with Vagrant providers other than VirtualBox
  # config.vm.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/app", "1"]

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "nodejs"
    chef.add_recipe "mongodb-debs"
    # chef.add_recipe "redis-server"
    chef.json = {
      "nodejs" => {
        "version" => "0.10.29"
        # uncomment the following line to force
	# recent versions (> 0.8.5) to be built from
	# the source code
	# , "from_source" => true
      }
    }
  end

  config.vm.provision :shell, :inline => "sudo apt-get install -y build-essential --no-install-recommends"
  config.vm.provision :shell, :inline => "sudo apt-get install -y redis-server --no-install-recommends"
  config.vm.provision :shell, :inline => "sudo apt-get install -y ruby1.9.1-dev --no-install-recommends"
  config.vm.provision :shell, :inline => "sudo apt-get install -y ruby1.9.3 --no-install-recommends"
  config.vm.provision :shell, :inline => "sudo gem install cf"
  
  config.vm.provision :shell, :inline => "sudo apt-get install -y git --no-install-recommends"
  config.vm.provision :shell, :inline => "sudo apt-get install -y tmux --no-install-recommends"
  
  # 安裝mono
  config.vm.provision :shell, :inline => "sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF"
  config.vm.provision :shell, :inline => "echo 'deb http://download.mono-project.com/repo/debian wheezy-libtiff-compat main' | sudo tee -a /etc/apt/sources.list.d/mono-xamarin.list"
  config.vm.provision :shell, :inline => "sudo apt-get update"
  config.vm.provision :shell, :inline => "sudo apt-get install -y mono-devel --no-install-recommends"
  
  # 安裝ZeroMQ 相關
  config.vm.provision :shell, :inline => "sudo apt-get install -y libtool --no-install-recommends"
  config.vm.provision :shell, :inline => "sudo apt-get install -y automake --no-install-recommends"
  config.vm.provision :shell, :inline => "sudo apt-get install -y pkg-config --no-install-recommends"
  
end
