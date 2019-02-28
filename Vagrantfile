Vagrant.configure('2') do |config|
  unless ENV['http_proxy'].nil?
    config.proxy.enabled  = true
    # set values from environmental variables
    config.proxy.http     = ENV['http_proxy']
    config.proxy.https    = ENV['http_proxy']
    config.proxy.no_proxy = ENV['no_proxy']
  end

  config.ssh.insert_key = false
  config.vm.synced_folder '.', '/vagrant'
  config.vm.box = 'bento/centos-7.4'
  config.vm.provision 'ansible_local' do |ansible|
    ansible.playbook = '/vagrant/ansible-dev.yml'
    ansible.verbose = 'v'
  end

  config.vm.provider 'virtualbox' do |v|
    v.memory = 1024
  end
end
