## Magento2 Vagrant Box
A simple way to get magento2 up and running. It consists of a ubuntu/trusty64 box provised via Ansible. 
The provider is Virtual Box. 
It will install 
 * Apache 2.4
 * PHP 5.6
 * MySql 5.6
 * GIT 
 * Swapfile
 * Composer


### Installation

1. Clone this repository: `git clone --recursive https://github.com/giappv/vagrant_magento2.git`
2. Navigate into the repository via `cd`
2. **IMPORTANT**: If you cloned the repository without the *--recursive* param, you need to initialize the required submodules: `git submodule update --init --recursive`
3. Start up virtual machine: `vagrant up`
4. Point a host name to 192.168.36.99 in /etc/hosts `echo '192.168.36.99 dev.m2' >> /etc/hosts`
5. Once the machine completes provisioning, SSH to the server (`vagrant ssh`).
6. Add your Magento Connect authentication credentials to ansible vars located at `ansible/vars/all.yml`
`repo.magento.com:
username: d7990a5019126a9e024d85f826f217f5
password: 935e734272ceee33becb5b01b6230d8b`
7. Go to /vagrant/htdocs/magento2 run `composer install`
8. Visit `dev.m2` on your browser to setup magento
9. Go to /vagrant/htdocs/magento2 run `php bin/magento setup:static-content:deploy` to update static folder

### Database Info
* Username: mage
* Password: 123456
* DB Name: mage

### Apache Doc Root
* /vagrant/htdocs/magento2 
