# packer-virtualbox
Build virtualbox image from Puppetlabs Vagrant box

```shell
wget --progress=dot -O virtualbox.box\
  https://atlas.hashicorp.com/puppetlabs/boxes/ubuntu-14.04-64-puppet/versions/1.0.3/providers/virtualbox.box
tar xvzf virtualbox.box \
  packer-ubuntu-14.04-x86_64-virtualbox-vagrant-puppet-1457717433-disk1.vmdk box.ovf
packer build packer-config.json
```

This will create an updated Virtual Box image.  To use the image, do the following:

```shell
vagrant up
```

If you get an error message like:

```
Failed to mount folders in Linux guest. This is usually because
the "vboxsf" file system is not available. Please verify that
the guest additions are properly installed in the guest and
can work properly. The command attempted was:

mount -t vboxsf -o uid=`id -u vagrant`,gid=`getent group vagrant | cut -d: -f3` vagrant /vagrant
mount -t vboxsf -o uid=`id -u vagrant`,gid=`id -g vagrant` vagrant /vagrant

The error output from the last command was:

stdin: is not a tty
/sbin/mount.vboxsf: mounting failed with the error: No such device
```

Log into the new node (with `vagrant ssh`) and run the following:

```shell
sudo /etc/init.d/vboxadd setup
```

Then run `vagrant reload`.
