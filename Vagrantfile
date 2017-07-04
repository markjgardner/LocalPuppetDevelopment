Vagrant.configure("2") do |config|
  config.vm.box = "puppetlabs/centos-7.2-64-puppet"
  config.vm.provision "puppet_server", run: "always" do |puppet|
    puppet.puppet_server = "10.0.2.2"
    puppet.puppet_node = "devnode"
  end
end
