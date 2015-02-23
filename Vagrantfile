VAGRANTFILE_API_VERSION = '2'

INSTANCE_MEMORY   = 1024
INSTANCE_CPU      = 1
INSTANCE_HOSTNAME = 'db-server'
INSTANCE_ADDRESS  = '192.168.33.2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'centos65-x86_64'
  # @see http://www.vagrantbox.es

  config.vm.provider :virtualbox do |vb|
    vb.customize [
      'modifyvm', :id,
      '--memory', INSTANCE_MEMORY.to_s,
      '--cpus',   INSTANCE_CPU.to_s,
      '--ioapic', 'on'
    ]
  end

  config.vm.define INSTANCE_HOSTNAME do |node|
    node.vm.hostname = INSTANCE_HOSTNAME
    node.vm.network :private_network, ip: INSTANCE_ADDRESS
  end

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook          = 'site.yml'
    ansible.inventory_path    = 'hosts_samples/hosts.vagrant'
    ansible.host_key_checking = false
  end
end
