Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.network "forwarded_port", guest: 80, host: 8080, gateway_ports: true, host_ip: "*"
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "site.yml"
    ansible.extra_vars = { ansible_ssh_user: "vagrant"}
    ansible.sudo = true
  end
end
