# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = 'jimdo-debian-6.0.7'
  config.vm.box_url = 'https://jimdo-vagrant-boxes.s3.amazonaws.com/jimdo-debian-6.0.7.box'
  config.vm.host_name = 'squeeze-sshuserconfig'

  config.vm.provision :shell, :privileged => false do |s|
    s.path = 'puppet-installer.sh'
    s.args = ['squeeze', '3.7.0-1puppetlabs1']
  end

  config.vm.provision :puppet do |puppet|
    puppet.module_path    = ENV.fetch('MODULES_PATH', nil)
    puppet.manifests_path = ENV.fetch('MANIFESTS_PATH', 'manifests')
    puppet.manifest_file  = ENV.fetch('MANIFEST_FILE', 'init.pp')
    puppet.options        = '--verbose --debug'
  end
end
