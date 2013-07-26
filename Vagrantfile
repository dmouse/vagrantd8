Vagrant.configure("2") do |config|
    # Every Vagrant virtual environment requires a box to build off of.
    config.vm.box = "precise64"

    # The url from where the 'config.vm.box' box will be fetched if it
    # doesn't already exist on the user's system.
    config.vm.box_url = "http://files.vagrantup.com/precise64.box"

    # Assign this VM to a host only network IP, allowing you to access it
    # via the IP.

    config.vm.network :private_network, ip: "192.168.50.2"
    config.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--memory", 768]
    end
    config.vm.hostname = "devbox.dev"

    # Provisioning settings.
    config.vm.provision :puppet do |puppet|
      puppet.manifests_path = "."
      puppet.manifest_file = "manifests/manifest.pp"
      puppet.module_path = "manifests/modules"
    end
    # The path to the platform
    config.vm.synced_folder "./web", "/var/www", :nfs => true
end