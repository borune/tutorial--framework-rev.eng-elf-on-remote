#How to setup the framework for reverse engineering an ELF executable from a MacOs
We will use `vagrant` to set up a virtual mashine running Ubuntu. Then use GDB to explore the program dynamicly. 
And lastly connnect a browser on the host (MacOs) to the GDBGUI on the remote (Ubuntu), for a more plesant GDB experience.


host: 
download installation from: https://www.vagrantup.com/


``` bash
mkdir your_dir_name
cd your_dir_name
vagrant init hashicorp/bionic64
```

host: add several lines to the Vagrant file and 
	  place your ELF file in the same dir
``` bash
vagrant up
vagrant provision
vagrant reload --provision
vagrant ssh
```


remote:
``` bash
gdbgui -r /vagrant/flag_checker
```



host:
``` bash
open -a firefox -g http://localhost:5050
```
