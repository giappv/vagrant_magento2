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
6. Add your Magento Connect authentication credentials to the global composer auth.json:

  * Open or create the file `~/.composer/auth.json`
  * Add the Magento Connect authentication credentials (if you don't have any, please check [here](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/connect-auth.html) on how to create them):

  ```json
  {
      "http-basic": {
          "repo.magento.com": {
              "username": "<public key>",
              "password": "<private key>"
          }
      }
  }
  ```
7. Go to /vagrant/htdocs/magento2 run `composer update`
8. Visit `dev.m2` on your browser to setup magento

### Database Info
* Username: mage
* Password: 123456
* DB Name: mage

### Guest Machine
* /vagrant/data/magento2 - Apache Document Root
