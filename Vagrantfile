Vagrant.configure(2) do |config|

  config.vm.box = "geerlingguy/centos7"
  config.ssh.insert_key = false
  N = 1
  VAGRANT_VM_PROVIDER = "virtualbox"
  ANSIBLE_RAW_SSH_ARGS = []
  SSH_PUB_KEY = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip

  #(1..N-1).each do |machine_id|
  #  ANSIBLE_RAW_SSH_ARGS << "-o IdentityFile=#{ENV["VAGRANT_DOTFILE_PATH"]}/machines/machine#{machine_id}/#{VAGRANT_VM_PROVIDER}/private_key"
  #end

  (1..N).each do |machine_id|
    config.vm.define "machine#{machine_id}" do |machine|
      machine.vm.hostname = "machine#{machine_id}"
      machine.vm.network "private_network", ip: "192.168.30.#{9+machine_id}"
      machine.vm.provider :virtualbox do |vitual|
        vitual.gui = false
        vitual.memory = 1024
        vitual.cpus = 1
    end
      machine.vm.provision "shell",
        inline: "sudo ifup enp0s8"
      machine.vm.provision 'shell', inline: "echo #{SSH_PUB_KEY} >> /home/vagrant/.ssh/authorized_keys"
      if machine_id == N
        machine.vm.provision :ansible do |ansible|
          ansible.playbook = "tests/test.yml"
          ansible.limit = 'all'
          ansible.inventory_path = "tests/inventory"
          #ansible.raw_ssh_args = ANSIBLE_RAW_SSH_ARGS
        end
      end

    end
  end

end
