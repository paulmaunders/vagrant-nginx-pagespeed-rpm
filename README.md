# vagrant-nginx-pagespeed-rpm
A vagrant file with ansible provisioning which I use on my Centos lab server to test my [ansible role to create an nginx rpm with pagespeed support](https://github.com/paulmaunders/ansible-role-nginx-pagespeed-rpm).
# Instructions
To use this vagrant environment, firstly clone the project, then run...
```
ansible-galaxy install -r requirements.yml
vagrant up
```
# Notes
## Installing Vagrant and vagrant-libvirt on Centos 7
To get vagrant running with libvirt on a Centos 7 machine you can use the following steps:
```
yum install https://releases.hashicorp.com/vagrant/1.7.4/vagrant_1.7.4_x86_64.rpm
yum -y install gcc ruby-devel rubygems
yum -y install libxslt-devel libxml2-devel libvirt-devel libguestfs-tools-c
vagrant plugin install vagrant-libvirt
echo 'VAGRANT_DEFAULT_PROVIDER=libvirt' >> /etc/environment
vagrant up
```
## Port forwarding
**NB**: I normally run this on a lab server and so I have enabled external port forwarding by default in the vagrant file. This means that any host on your network will be able to access nginx on the vagrant box through port 8080. You can disable this by setting the gateway_ports option to false in the Vagrant file.
```
 config.vm.network "forwarded_port", guest: 80, host: 8080, gateway_ports: true, host_ip: "*"
```
