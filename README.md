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
```sh
vagrant suspend
```
