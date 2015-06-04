# Long Beach i-Team Developer Setup

This README goes over the steps required to get a basic virtual machine (VM) running with a full stack web development enviornment on your City issued Windows computer.

## Overview
1. Submit a Technology Service Request (TSR) to get temporary admin rights for your Windows account
2. Play nice with the City's proxy
3. Install required software/toolset
4. Download and run your Vagrant VM

## Submit a Technology Service Request (TSR)
Submit a completed TSR to [TS.Support@longbeach.gov](mailto:TS.Support@longbeach.gov) that lists required software that needs to be installed. In the description of the form, be sure to emphasize that you need temporary admin rights to install and configure free/open source software.

## Proxy Configuration
1. Download and install [Microsoft's Firewall Client for ISA Server](https://www.microsoft.com/en-us/download/details.aspx?id=10193)
2. Configure Firewall Client for ISA Server with the hostname `proxy1` on port `80` and authenticate with your Windows desktop credentials. This is required as the City's proxy uses NTLM authentication.

## Required Software
Download and install the following software:

1. [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
2. [Vagrant](https://www.vagrantup.com/)
3. [Cygwin](https://www.cygwin.com/)
	-  Mark __ssh__ and __rsync__ for installation
	-  Add cygwin's bin directory to your path 
4. Your code editor of choice (Atom, Sublime Text, Notepad++, etc.)

## Vagrant
1. Checkout this directory into your machine, open command line, and `cd` into this checked out repository
3. Install the vagrant-proxyconf plugin: `vagrant plugin install vagrant-proxyconf`
4. Use the following Vagrantfile (latest version is on Bitbucket)
5. Install the vagrant-rsync-back plugin: `vagrant plugin install vagrant-rsync-back`
6. `vagrant up` to boot your VM
7. `vagrant rsync-auto` to configure sync from host to client
8. Open a new console and `vagrant ssh` to login to your VM
10. Enjoy! More Vagrant commands can be found [here](http://docs.vagrantup.com/v2/cli/index.html)
11. Type `vagrant rsync-back` to sync from client to host; which will be useful if you were to create new projects on the client VM

### Vagrantfile
The Vagrantfile is a script that configures and provisions the VM. To modify the software that is installed on the VM, modify the SHELL script and provisioning portion of this file.