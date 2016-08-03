# Ansible

## Install on Linux

sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible

## Install on Mac OSX

Pre-requirement: any python install.
sudo easy_install pip
sudo pip install ansible

If ansible gives errors related to setuptools, run the following:
pip install --upgrade setuptools --user python

# Vagrant

## Install

### VirtualBox

sudo apt-get install virtualbox

Install the dkms package to ensure that the VirtualBox host kernel modules
(vboxdrv, vboxnetflt and vboxnetadp) are properly updated if the Linux kernel
version changes during the next apt-get upgrade.

sudo apt-get install virtualbox-dkms

### Vagrant

Don't install using apt-get. Install the very last version from Vagrant
website, else plugins won't work.

sudo dpkg -i vagrant-downloaded-package

### Vagrant Plugins

vagrant plugin update
vagrant plugin install vagrant-vbguest

### Get SSH connection details (informative only)

vagrant ssh-config

### Connect Vagrant by plain ssh (informative only)

ssh -p 2222 -i /[project-root-dir]/.vagrant/machines/default/virtualbox/private_key vagrant@127.0.0.1

# Ansible execute commands on remote servers (informative only)

ansible testserver -m ping
ansible testserver -m command -a uptime
ansible testserver -s -m apt -a name=nginx
ansible testserver -s -m service -a "name=nginx state=restarted"

# Get Project running

1. Clone git repo
2. Checkout the correct branch
3. Review /Vagrantfile IPs and ports (existing values are default ones)
4. Review /ansible/hosts IPs and ports (existing values are default ones)
5. Review /ansible/files/variables.yml and fill your preferences
6. Copy /ansible/files/local.parameters.yml.example to /ansible/files/local.parameters.yml and setup it properly
7. Get confortable and type: $ vagrant up
8. After provision finish reload Vagrant by $ vagrant reload
9. Map Project host name to Vagrant IP address on /etc/hosts
10. Enjoy!
