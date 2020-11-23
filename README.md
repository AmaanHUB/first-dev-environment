# First Dev Environment With Virtual Machines and Vagrant

## Vagrant

* Initialise vagrant in the directory, creates a `Vagrantfile`, when done without specifying with VM want to use
```sh
vagrant init

# otherwise downloading box too, name on Hashicorp Vagrant website

vagrant init <boxname>
```

### Boxes

* Preloaded vagrant files that create the virtual machine.
	* Usually just for a specific OS (.e.g. Ubuntu, Arch, Fedora), headless or desktop version
		* Headless tends to be faster due to being lighter

* In the`Vagrantfile`, change to the box that you want to use, such as:
```ruby
Vagrant.configure("2") do |config|

#  config.vm.box = "<boxname>"
  # here is what you would change it to
  config.vm.box = "ubuntu/xenial64"
```

* Afterwards can start the machine with:
```sh
vagrant up
```

* One can stop the machine and remove all the resources that it was using:
```sh
vagrant destroy
```

* To access the machine with ssh:
```sh
vagrant ssh
```

* Suspend the machine with:
```
vagrant suspend
```

* Create a private network with an IP address to connect to:
```ruby
Vagrant.configure("2") do |config|

# config.vm.network "private_network", ip: "ip_address"
  config.vm.network "private_network", ip: "192.168.33.10"
```

* Reload the VM without deleting it:
```
vagrant reload
```

* Assign the IP as an easy to remember URL
	* First install the `hostsupdater` plugin:
```
vagrant plugin install hostspluginupdater
```
	* Add to the `Vagrantfile` to call the plugin and direct where you want it to point (can be underneath the private network section):
```ruby
  config.vm.hostname = "development.local"
```
		* N.B. This changes the host machines /etc/hosts so requires the sudo password. It should be deleted from this when the machine is destroyed or suspened, unless specified otherwise

### Simple Commands In Ubuntu

* Update and upgrade:
```sudo apt update && sudo apt upgrade```

*
