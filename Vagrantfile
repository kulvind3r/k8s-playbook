nodes = [
  { :hostname => 'centos78vm1', :ip => '192.168.0.41', :box => 'centos78' },
  { :hostname => 'centos78vm2', :ip => '192.168.0.42', :box => 'centos78' }
]

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      nodeconfig.vm.box = node[:box]
      nodeconfig.vm.hostname = node[:hostname]
      nodeconfig.vm.network :private_network, ip: node[:ip]

      memory = node[:ram] ? node[:ram] : 4096;
      nodeconfig.vm.provider :virtualbox do |vb|
        vb.customize [
          "modifyvm", :id,
          "--cpuexecutioncap", "50",
          "--memory", memory.to_s,
          "--cpus", "2"
        ]
      end
    end
  end
end
