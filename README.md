# Long Beach Innovation Team: Developer Setup

## Overview
1. Submit a Technology Service Request (TSR) to get temporary admin rights
2. Install required software/toolset
3. Play nice with the City's proxy
4. Install software required to run a virtual environment using Vagrant/Virtualbox
5. Install miscellaneous tools

## Submitting a Technology Service Request (TSR)
Submit a TSR with completed request listing required software that needs to be installed. In the description of the form, mention that you need temporary admin rights to install and configure free/open source software.

## Proxy Configuration
1. Download and install [Microsoft's Firewall Client for ISA Server](https://www.microsoft.com/en-us/download/details.aspx?id=10193)
2. Configure Firewall Client for ISA Server with the hostname `proxy1` on port `80` and authenticate with your Windows desktop credentials. This is required as the City's proxy uses NTLM authentication.

## Python
1. Open command line (cmd.exe): SET TRUST_ENV=False SET NO_PROXY=pypi.python.org (or SET NO_PROXY=1)
2. Create directory called `Projects` directly under your user directory, e.g. `C:\Users\<YOUR USERNAME>\Projects`
3. `cd C:\Users\<YOUR USERNAME>\Projects`
4. `virtualenv iteam_pyweb` (or whatever you want)
5. Activate environment `iteam_pyweb\Scripts\activate`
6. Install django: `pip install django`

## Meteor
- Install the Meteor JS framework with the windows installer found at [their site](https://www.meteor.com/)
- Move on to Vagrant (might have to setup a dev enviornment with this instead)

## Vagrant
- Install the vagrant-proxyconf plugin: vagrant plugin install vagrant-proxyconf
- Use the following Vagrantfile (latest version is on Bitbucket)
- Install cygwin, install ssh and rsync, and add cygwin's bin directory to path
- Install https://github.com/smerrill/vagrant-rsync-back
- `vagrant up`
- `vagrant rsync-auto` to configure sync from host to client
- Open a new console
- `vagrant ssh`
- Enjoy!
- Type `vagrant rsync-back` to sync from client to host