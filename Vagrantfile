nodes = [
  { :hostname => 'centos78vm1', :ip => '192.168.0.41', :cpu => '2', :ram => '2048', :box => 'kulvind3r/centos78' },
  { :hostname => 'centos78vm2', :ip => '192.168.0.42', :cpu => '2', :ram => '4096', :box => 'kulvind3r/centos78' }
]

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      nodeconfig.vm.box = node[:box]
      nodeconfig.vm.hostname = node[:hostname]
      nodeconfig.vm.network :private_network, ip: node[:ip]

      memory = node[:ram] ? node[:ram] : 4096;
      cpu = node[:cpu] ? node[:cpu] : 2;

      nodeconfig.vm.provider :virtualbox do |vb|
        vb.customize [
          "modifyvm", :id,
          "--cpuexecutioncap", "50",
          "--memory", memory.to_s,
          "--cpus", cpu.to_s
        ]
      end
    end
  end
end
