Vagrant.configure("2") do |config|


  servers=[
    {
      :hostname => "ServerAA",
      :box => "ubuntu/bionic64",
      :ip => "192.168.56.2",
      :ssh_port => "2200"
      #:web_port => "8082"
    },

    {
      :hostname => "ServerBB",
      :box => "ubuntu/bionic64",
      :ip => "192.168.56.3",
      :ssh_port => "2201"
      #:web_port => "8083"
    },

    {
      :hostname => "ServerCC",
      :box => "ubuntu/bionic64",
      :ip => "192.168.56.4",
      :ssh_port => "2202"
      #:web_port => "8084"
    }
  ]

  servers.each do |machine|
    config.vm.define machine[:hostname] do |node|
      node.vm.hostname = machine[:hostname]
      node.vm.provision :shell, path: "sh.sh"
      node.vm.box = machine[:box]
      node.vm.network "private_network",ip: machine[:ip]
      node.vm.network "forwarded_port", guest: 22, host:machine[:ssh_port], id:"ssh"
      #node.vm.network "forwarder_port", guest: 80, host:machine[web_port], id:"http"
        node.vm.provider "virtualbox" do |vb|
          vb.memory = 1094
          vb.cpus = 1
       end
    end
  end
end