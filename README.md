# How to setup a framework for reverse engineering an ELF executable from a macOS
We will use `vagrant` to set up a virtual machine running Ubuntu. Then use GDB to explore the program dynamicly.
And lastly connect a browser on the host (MacOs) to the GDBGUI on the remote (Ubuntu), for a more pleasant GDB experience.

## host:

download installation from: https://www.vagrantup.com/ and follow the instructions.

Or:

``` bash
curl -O https://releases.hashicorp.com/vagrant/2.2.7/vagrant_2.2.7_x86_64.dmg
sudo hdiutil attach vagrant_2.2.7_x86_64.dmg
sudo installer -package /Volumes/vagrant_2.2.7_x86_64/vagrant_2.2.7_x86_64.pkg -target /
sudo hdiutil detach /Volumes/vagrant_2.2.7_x86_64
rm vagrant_2.2.7_x86_64.dmg
```

Make your image in a folder.

``` bash
mkdir your_dir_name
cd your_dir_name
vagrant init hashicorp/bionic64
```

- Overwrite Vagrant file with the one in this repo
- Place your ELF file in the same dir

``` bash
vagrant up
vagrant provision
# vagrant reload --provision
vagrant ssh
```

## remote:

``` bash
gdbgui -r /vagrant/flag_checker
```

## host:

``` bash
open -a firefox -g http://localhost:5050
```
