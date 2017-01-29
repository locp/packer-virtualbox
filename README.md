# packer-virtualbox
Build virtualbox image from Puppetlabs Vagrant box

```shell
wget --progress=dot -O virtualbox.box\
  https://atlas.hashicorp.com/puppetlabs/boxes/ubuntu-14.04-64-puppet/versions/1.0.3/providers/virtualbox.box
tar xvzf virtualbox.box \
  packer-ubuntu-14.04-x86_64-virtualbox-vagrant-puppet-1457717433-disk1.vmdk box.ovf
packer build packer-config.json
```
