# On Linux #

## 1. Install tools ##
> To complete this task, you need to install the necessary software.
> Each chapter shows the steps of installing components, links to sites with additional information, and author's comments.

#### 1.1 Install VirtualBox and VagrantBox ####
For install Vagrant and Virtual box you can use next lines in your terminal window (using ctrl+alt+T):
```ch
    $ sudo apt update
    $ sudo apt install virtualbox  
    $ curl -O https://releases.hashicorp.com/vagrant/2.2.19/vagrant_2.2.19_x86_64.deb   
    $ sudo apt install ./vagrant_2.2.9_x86_64.deb
```
Good article about installing virtualbox and vagrantbox:
- [Install and Use VirtualBox in Ubuntu 20.04]
- [Download Vagrant]
- [Setting Up Vagrant Box]
- [Installing VirtualBox and Vagrant on Ubuntu]

#### 1.2 Create a project folder ####
After you need to create a separate folder that will contain the necessary documents.
```ch
    $ mkdir Project_1
    $ cd ./Project_1/
```
#### 1.3 Install Python and pip ####
Firstly, you need to install python.
To see which version of Python 3 you have installed, open a command prompt and run:
```ch
    $ python3 --version
```
After you can easily install Python different versions, example 3.9 with the following commands:
```ch
    $ sudo apt-get update
    $ sudo apt-get install python
    $ sudo apt-get install python3.9
```
If you want to use a more current Python, we recommend using the deadsnakes PPA to install Python 3.8:
```ch
    $ sudo apt-get install software-properties-common
####    $ sudo add-apt-repository ppa:deadsnakes/ppa
    $ sudo apt-get update
    $ sudo apt-get install python3.8
```
Python 2.7.9 and later (on the python2 series), and Python 3.4 and later include pip by default.
To see if pip is installed, open a command prompt and run:
```ch
    $ command -v pip
    $ pip3 --version
```
If pip isn’t already installed, then install pip for Python 3 run the following commands as root or sudo user in your terminal:
```ch
    $ sudo apt update
    $ sudo apt install python3-pip
```
To install pip, follow t2.2he official pip installation guide - this will automatically install the latest version of setuptools.
Good article about installing python and pip:
- [Properly Installing Python]
- [Official pip installation guide]
- [Python Packaging User Guide]
- [New Python Versions]

#### 1.4 Install Virtualenv
Next, you need to install and create your virtualenv. For install you can use next line:
```ch
    $ sudo apt-get install python3-venv -y
```
For create your virtual environment use next lines:
```ch
    $ cd ./Project_1/
    $ python3 -m venv devsecops
    $ source devsecops/bin/activate
    # Install packages
    $ pip install -r requirements.txt
```
Good article about installing virtualenv:
- [Installation]
- [How to create python 3 virtual environment]
- [How to set up python virtual environment]

The Ansible installation will be installed in the Create/Setting Virtualenv section.

   [Install and Use VirtualBox in Ubuntu 20.04]: https://linuxhint.com/install_use_virtualbox_ubuntu/
   [Download Vagrant]: https://www.vagrantup.com/downloads
   [Setting Up Vagrant Box]: https://el8-lab.all-open.com/setup/vagrant/
   [Installing VirtualBox and Vagrant on Ubuntu]: https://fabianlee.org/2017/04/03/virtualbox-installing-virtualbox-and-vagrant-on-ubuntu-14-0416-04/
   [Properly Installing Python]: https://docs.python-guide.org/starting/installation/
   [Official pip installation guide]: https://pip.pypa.io/en/stable/installation/#ensurepip
   [Python Packaging User Guide]: https://packaging.python.org/en/latest/tutorials/installing-packages/#creating-and-using-virtual-environments
   [New Python Versions]: https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa
   [Installation]: https://virtualenv.pypa.io/en/latest/installation.html
   [How to create python 3 virtual environment]: https://linoxide.com/how-to-create-python-virtual-environment-on-ubuntu-20-04/
   [How to set up python virtual environment]: https://itnext.io/how-to-set-up-python-virtual-environment-on-ubuntu-20-04-a2c7a192938d
   [Install Ansible by using virtualenv]: https://clouddocs.f5.com/products/orchestration/ansible/devel/usage/virtualenv.html


## 2. Create/Setting Virtualenv ##

#### Check version. ####

Before you go any further, make sure you have [Python](https://docs.python.org/3.9/), [Pip](https://pip.pypa.io/en/stable/), [Virtualenv](https://virtualenv.pypa.io/en/20.0.17/) and that it’s available from your command line.

 You can check this by simply running:

```sh
python --version
```
```sh
pip --version
```
```sh
virtualenv --version
```

> Python should be 3.9.*, pip == 20.0.2, virtualenv ==	20.0.17.

#### Create a virtual environment. ####

For start you should create directory with this and future Virtualenv folders.

 Create folder in your home directory:

```sh
mkdir ~/environments
```
> mkdir - command for create folder

> environments - folder name

 Create a virtual environment:

```sh
virtualenv -p /usr/bin/python3.9 ~/environments/python3.9
```
> /usr/bin/python3.9 - your local path to python3.9

> ~/environments/python3.9 - folder name with a virtual environment

> [good article about venv](https://realpython.com/python-virtual-environments-a-primer/)

#### Active your virtual environment. ####

 To begin using the virtual environment, it needs to be activated:

```sh
source ~/environments/python3.9/bin/activate
```

#### Install Ansible. ####

 Install Ansible:2.9.6 using requirements files:

```sh
pip install -r <path to requirements.txt>
```

 You can use install Ansible:2.9.6 without using requirements file:

```sh
pip install ansible==2.9.6
```

You cat reed about install Python packages in [this article](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/).

#### Deactivate. ####

If you are done working in the virtual environment for the moment, you can deactivate it:

```sh
deactivate
```

# 3. Ansible #
***Ansible Automation Platform is the IT automation technology that anyone can use***
***More information [here](https://www.ansible.com/products/automation-platform/).***

##### For use Ansible correctly we need 2 files: #####

### playbook.yml ###
```sh
---
- hosts: ntp		
  become: true		
  tasks:
    - name: Update OS		
      package:
        name: '*'
        state: latest

    - name: Make sure Chrony is started up
      service:
        name: chronyd
        state: started
        enabled: yes

    - name: Replace line in config file		
      lineinfile:
        path: /etc/chrony.conf
        regexp: '^pool(.*)'
        line: 'server sth1.ntp.se \n server sth2.ntp.se'
        backrefs: yes       

    - name: Restart chronyd.service		
      shell: systemctl restart chronyd.service
```
**Description:**
- hosts: - name used group descripted in inventory file.
- become:true - gives rights of root
- tasks: - name and description of tasks
- Update OS(task) - update system to last version
- Make sure Chrony is started up(task) - check chrony is started
- Replace line in config file(task) -   set new ntp server
- Restart chronyd.service(task) - reboot chrony for the changes to take effect

### inventory ###
```sh
[ntp]		
ntp.edu.tentixo.com ansible_ssh_host=192.168.1.100 ansible_ssh_port=22 ansible_ssh_user=vagrant
ansible_ssh_private_key_file=/home/arthur/courses/DevOps-Security/.vagrant/machines/ntp.edu.tentixo.com/virtualbox/private_key
```
**Description:**
- [ntp] - name group used  in playbook.yml file.
- ansible_ssh_host - ip of virtual server
- ansible_ssh_port - port of virtual server
- ansible_ssh_user - root user name of virtual server
- ansible_ssh_private_key_file - path to your private key(should chenge {path to project holder} to path to your project)
-
**Links:**
1. https://www.ansible.com/products/automation-platform
2. https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html
3. https://www.redhat.com/en/topics/automation/what-is-an-ansible-playbook
4. https://docs.ansible.com/ansible/latest/network/getting_started/first_inventory.html
