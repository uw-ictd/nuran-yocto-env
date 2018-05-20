# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.define :yocto, autostart: true do |machine|
    machine.vm.box = "ubuntu/xenial64"
    machine.vm.hostname = "yocto"
    machine.vm.synced_folder "./" , "/home/vagrant/yocto", type: "virtualbox"

    # Forward the host SSH agent to allow fetching upstream repos.
    machine.ssh.forward_agent = true

    # The virtual machine has relatively high resource requirements
    # for a performant build.
    machine.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "8192"]
      vb.customize ["modifyvm", :id, "--cpus", "3"]
    end
    machine.disksize.size = "50GB"

    machine.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.extra_vars = {
        # Ubuntu server 18.04+ does not come with python2
        ansible_python_interpreter: "/usr/bin/python3"
      }
      ansible.host_key_checking = false
      ansible.playbook = "ansible/nuran-litecell-build-env.yml"
      ansible.raw_arguments = ['--timeout=20']
      ansible.verbose = 'v'
    end
  end

end
