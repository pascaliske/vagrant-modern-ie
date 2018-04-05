# -*- mode: ruby -*-
# vi: set ft=ruby :

# auto install plugins
required_plugins = %w[vagrant-atomic]
required_plugins.each do |plugin|
  exec "sudo vagrant plugin install #{plugin};vagrant #{ARGV.join(' ')}" unless Vagrant.has_plugin? plugin || ARGV[0] == 'plugin'
end

boxes = [
  { name: 'ie8-win7', box: 'IE8-Win7' },
  { name: 'ie9-win7', box: 'IE9-Win7' },
  { name: 'ie10-win7', box: 'IE10-Win7' },
  { name: 'ie11-win7', box: 'IE11-Win7' },
  { name: 'ie11-win81', box: 'IE11-Win81' },
  { name: 'msedge-win10', box: 'MSEdge-Win10' }
]

Vagrant.configure('2') do |config|
  boxes.each do |box|
    next unless File.exists?(URI.escape("#{box[:box]}.box"))

    config.vm.box_url = URI.escape("#{box[:box]}.box")
    config.vm.box = box[:name]
    config.ssh.username = 'IEUser'
    config.ssh.password = 'Passw0rd!'

    config.vm.define box[:name], autostart: false do |machine|
      machine.vm.box = box[:name]
      machine.vm.hostname = box[:name]
      config.vm.provider :virtualbox do |vb|
        vb.name = box[:name]
        vb.gui = true
        vb.memory = '1024'
        vb.customize ['modifyvm', :id, '--memory', '1024']
        vb.customize ['modifyvm', :id, '--vram', '128']
        vb.customize ['modifyvm', :id, '--cpus', '2']
        vb.customize ['modifyvm', :id, '--ioapic', 'on']
        vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
        vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
      end
    end
  end
end
