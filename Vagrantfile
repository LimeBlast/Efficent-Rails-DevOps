# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "relativkreativ/centos-7-minimal"
  config.vm.network "public_network", ip: "192.168.1.100"

  config.vm.provision "shell" do |shell|
    ssh_public_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip

    shell.inline   = <<-END
      mkdir -p -m 0700 /root/.ssh
      echo "#{ssh_public_key}" > /root/.ssh/authorized_keys chmod 0600 /root/.ssh/authorized_keys
    END
  end
end
