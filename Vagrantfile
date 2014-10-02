# -*- mode: ruby -*-
# vi: set ft=ruby :


ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Enable SSH agent forwarding
  config.ssh.forward_agent = true

  # Load configuration
  raise Vagrant::Errors::VagrantError.new, "Error: configuration file _config.yml.default not found" unless File.exist?("_config.yml.default")
  settings = YAML::load_file("_config.yml.default")
  settings = settings.merge(YAML::load_file("_config.yml")) if File.exist?("_config.yml")

  # Define default box
  config.vm.box = "hashicorp/precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.hostname = settings['vm']['hostname']
  config.vm.network :private_network, ip: settings['vm']['ip_address']

  # Enable symlinks on shared folder (otherwise no installation)
  config.vm.provider :virtualbox do |vb|
    vb.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]
  end

  # Override box for VMWare Fusion
  config.vm.provider :vmware_fusion do |v, override|
    override.vm.box = "vmware_fusion"
    override.vm.box_url = "http://files.vagrantup.com/precise64_vmware_fusion.box"
  end

end
