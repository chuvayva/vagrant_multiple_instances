VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false

  host = 'db'
  config.vm.define host do |db|
    db.vm.box = 'ubuntu/trusty64'
    db.vm.hostname = host
    db.vm.network :private_network, ip: '192.168.0.5'

    db.vm.provision :hosts, :sync_hosts => true # need vagrant-hosts plugin
  end

  host = 'web'
  config.vm.define host do |web|
    web.vm.box = 'ubuntu/trusty64'

    web.vm.provider "virtualbox" do |v|
      v.memory = 1500
    end

    web.vm.hostname = host
    web.vm.network :private_network, ip: '192.168.0.6'

    web.vm.provision :hosts, :sync_hosts => true # need vagrant-hosts plugin

    web.vm.provision 'ansible' do |ansible|
      ansible.limit = 'all'
      ansible.playbook = 'play.yml'

      ansible.groups = {
        'web' => ['web'],
        'db'  => ['db']
      }
    end
  end

end
