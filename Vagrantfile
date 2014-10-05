# -*- mode: ruby -*-
# vi: set ft=ruby :


ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Add Chef to the bare box using Vagrant plugin
  unless Vagrant.has_plugin?("vagrant-omnibus")
    raise Vagrant::Errors::VagrantError.new, "Error: missing plugin. Please run 'vagrant plugin install vagrant-omnibus'"
  end
  config.omnibus.chef_version = :latest

  # Add Librarian-Chef to the bare box using Vagrant plugin
  unless Vagrant.has_plugin?("vagrant-librarian-chef")
    raise Vagrant::Errors::VagrantError.new, "Error: missing plugin. Please run 'vagrant plugin install vagrant-librarian-chef'"
  end
  config.librarian_chef.cheffile_dir = ".chef"

  # Enable SSH agent forwarding
  config.ssh.forward_agent = true

  # Load settings
  raise Vagrant::Errors::VagrantError.new, "Error: configuration file _config.yml not found" unless File.exist?("_config.yml")
  settings = YAML::load_file("_config.yml")

  # Default box configuration
  config.vm.box = "puppetlabs/ubuntu-14.04-64-nocm"
  config.vm.box_url = "https://vagrantcloud.com/puppetlabs/boxes/ubuntu-14.04-64-nocm/versions/3/providers/virtualbox.box"

  config.vm.hostname = settings['vm']['hostname']
  config.vm.network :private_network, ip: settings['vm']['ip_address']

  # Do not mount /vagrant, mount local blogs directory to /blog instead
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "blogs", "/blogs", create: true, owner: 'vagrant', group: 'vagrant'

  # Provision vm using Chef-Librarian
  config.vm.provision :chef_solo do |chef|
    chef.custom_config_path = '.chef/config.rb'
    chef.cookbooks_path = ".chef/cookbooks"
    chef.json.merge!(JSON.parse(File.read(".chef/node.json")))
  end

  # Make the vm work using VMWare Workstation too
  config.vm.provider :vmware_desktop do |v, override|
    override.vm.box = "puppetlabs/vmware_desktop"
    override.vm.box_url = "https://vagrantcloud.com/puppetlabs/boxes/ubuntu-14.04-64-nocm/versions/3/providers/vmware_desktop.box"
  end

  # Make vm work using VMWare Fusion too
  config.vm.provider :vmware_fusion do |v, override|
    override.vm.box = "puppetlabs/vmware_fusion"
    override.vm.box_url = "https://vagrantcloud.com/puppetlabs/boxes/ubuntu-14.04-64-nocm/versions/3/providers/vmware_fusion.box"
  end

  # @todo:
  # - git version 2.1 (http://tecadmin.net/install-git-on-ubuntu/)

end
