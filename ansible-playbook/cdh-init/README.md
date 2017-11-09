# Initializing cdh node using ansible playbook

## Requirement
ansible >= 2.3  
jinja2(python-jinja2)  
PyYAML(python-yaml)  
paramiko(python-paramiko)  
pycrypto >= 2.6 (python-crypto)  
setuptools(python-setuptools)    

```bash
# install requirements
$ sudo apt-get install -y python-jinja2 python-yaml python-paramiko python-crypto python-setuptools
```  

```bash
# install ansible
$ tar xvfz ansible-2.3.2.0-1.tar.gz
$ cd ansible-2.3.2.0-1
$ sudo python setup.py build
$ sudo python setup.py install
$ ansible --version
ansible 2.3.2.0
  config file = 
  configured module search path = Default w/o overrides
  python version = 2.7.12 (default, Nov 19 2016, 06:48:10) [GCC 5.4.0 20160609]
```  

## Tasks
roles/common/tasks/main.yml  

## Inventory
inventory/inventory.cfg

## Run 
```bash
$ ansible-playbook -i inventory/inventory.cfg cdh-init.yml -b -v
```  
