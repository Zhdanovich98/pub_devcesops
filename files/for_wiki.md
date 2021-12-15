<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#On-Linux ">On Linux </a></li>
    <ul>
        <li><a href="#Install-tools">Install tools</a></li>
      </ul>
    <li><a href="#Help">Help</a></li>
  </ol>
</details>

# On Linux #

**This project works with:**
| Tools | Version |
| ------ | ------ |
| Linux Ubuntu | 20.04 |
| Linux RHEL | 8 |
| Python | 3.8.10 or 3.9.5 |
| Virtualenv | 20.0.17 |
| VirtualBox | 6.1.26 |
| Vagrant | 2.2.6 |
| Ansible | 2.9.6 |

***On other Linux families and packages has not been tested!!!***

## Install tools ##
> To complete this task, you need to install the necessary software.
> Each chapter shows the steps of installing components, links to sites with additional information, and author's comments.

### Install VirtualBox and VagrantBox ###
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

### Create a project folder ###
After you need to create a separate folder that will contain the necessary documents.
```ch
    $ mkdir Project_1
    $ cd ./Project_1/
```
### Install Python and pip ###
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

### Install Virtualenv ###
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

The Ansible installation will be installed in the **Create/Setting Virtualenv** section.

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


## Create/Setting Virtualenv ##

### Check version. ###

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

### Create a virtual environment. ###

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

### Active your virtual environment. ###

 To begin using the virtual environment, it needs to be activated:

```sh
source ~/environments/python3.9/bin/activate
```

### Install Ansible. ###

 Install Ansible:2.9.6 using requirements files:

```sh
pip install -r <path to requirements.txt>
```

 You can use install Ansible:2.9.6 without using requirements file:

```sh
pip install ansible==2.9.6
```

You cat reed about install Python packages in [this article](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/).

### Deactivate. ###VirtualBox

If you are done working in the virtual environment for the moment, you can deactivate it:

```sh
deactivate
```

##  Vagrantfile:

   [Link on official Docs for Vagrant](https://www.vagrantup.com/docs/vagrantfile)
            ```
            Vagrant.configure("2") do |config|
                  ##### VM definition #####   
                  config.vm.define "ntp.edu.tentixo.com" do |config|          
                  config.vm.hostname = "ntp.edu.tentixo.com"                  
                  config.vm.box = "generic/rhel8"                             
                  config.vm.network "private_network", ip: "172.28.128.22"    
                  config.vm.box_check_update = false                         

                  config.vm.provision :ansible do |ansible|
                        ansible.playbook = "provision.yaml"                   
                        ansible.inventory_path = "inventory"                  
                  end

                  config.vm.provider "virtualbox" do |v|                      
                        v.memory = 2048                                       
                        v.cpus = 2                                            
                        end
                  end
            end
            ```

  **Description:**
  - config.vm.define - Description of server name and config name
  - config.vm.hostname - Hostname definition
  - config.vm.box - Specifying the image that the vagrant will use and deploy
  - config.vm.network - Description of the network type, specifying the ip of the machine
  - config.vm.provision - Description of provision, its type and config name
  - config.vm.provider - Provider selection and its config

## Ansible ##
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

## Official Links: ##
##### - [Information about Python](https://docs.python.org/3.9/)
##### - [Information about Ansible](https://www.ansible.com/)
##### - [Information about VagrantBox](https://www.vagrantup.com/)
##### - [Information about VirtualBox](https://www.virtualbox.org/)
##### - [Information about VirtualEnv](https://virtualenv.pypa.io/en/20.0.17/)
##### - [Information about RHEL8](https://www.redhat.com/en/enterprise-linux-8)


___

# On Windows #

**This project works with:**
| Tools | Version |
| ------ | ------ |
| Windows 10 | +19042.928 |
| Linux RHEL | 8 |
| VirtualBox | +6.1.22 (Windows version) |
| WSL | 2 |
| Python | 3.8.10 |
| Virtualenv | 20.0.17 |
| Vagrant | 2.2.18 |
| Vagrant plugin: virtualbox_WSL2 | 0.1.3 |
| Ansible | 2.9.6 |

***On other Windows versions and packages has not been tested!!!***

##  Install tools: ##
###  Install Vagrant and VirtualBox ###
 * You need to go to the virtualbox [website](https://www.virtualbox.org/wiki/Downloads) and download the latest version for Windwos(I have it 6.1.30)<br>
 * You need to go to the vagrant [website](https://www.vagrantup.com/downloads) and download the last version(for you processor 32/64-bit) for Windows(I have it 2.2.19 for 64-bit)

### Install WSL2 ###
   You must use WSL2. To install it, check the official documentation.<br>
   You need to turn on components WSL 10 using dism: <br>
   ```
   dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
   dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestar
   ```
   or using PowerShell: <br>
   ```
   Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
   Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform
   ```
   and then restart you PC;<br>
   Hardware virtualization support must be enabled in the BIOS / UEFI setup of the computer. <br>
   After these steps you need to update WSL for WSL 2 version. To do this, you need to go to the [website](https://docs.microsoft.com/ru-ru/windows/wsl/wsl2-kernel) and download    the wsl_update_x64.msi file, install it. <br>

   To make WSL2 the default architecture for new distributions, in PowerShell run the command:<br>
   ```
   wsl --set-default-version 2
   ```
   Then you need to install distribution (i have it Ubuntu 20.04).<br>
   And you can check the used WSL version in PowerShell using the command:<br>
   ```
   wsl -l -v
   ```
   if you don't see WSL version 2, you need using this comand:<br>
   ```
   wsl --set-version Ubuntu-20.04 2
   ```

### Install Vagrant inside WSL2 ###
   Assuming you're using Ubuntu 20.04, run:
   ```
   # run inside WSL 2
   # check https://www.vagrantup.com/downloads for more info
   curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
   sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
   sudo apt-get update && sudo apt-get install vagrant
   ```
   Then, you must enable WSL 2 support. To do that, append two lines into the ~/.bashrc file: <br>
   ```
   # append those two lines into ~/.bashrc
   echo 'export VAGRANT_WSL_ENABLE_WINDOWS_ACCESS="1"' >> ~/.bashrc
   echo 'export PATH="$PATH:/mnt/c/Program Files/Oracle/VirtualBox"' >> ~/.bashrc
   # now reload the ~/.bashrc file
   source ~/.bashrc
   ```

### Install virtualbox_WSL2 plugin ###
   If you have problem with Vagrant like this:
   ```
   Bringing machine 'default' up with 'virtualbox' provider...
==> default: Checking if box 'hashicorp/bionic64' version '1.0.282' is up to date...
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection refused. Retrying...
    default: Warning: Connection refused. Retrying...
    default: Warning: Connection refused. Retrying...
    default: Warning: Connection refused. Retrying...
    default: Warning: Connection refused. Retrying...
    default: Warning: Connection refused. Retrying...
==> default: Waiting for cleanup before exiting...
   ```
   You need install plugin:
   ```
  $ vagrant plugin install virtualbox_WSL2
   ```
###  Create project folder:
   Go to the required directive and create project folder:
   ```
   $ mkdir VagrantVM
   $ cd ./VagrantVM/
   ```
## Create your virtualenv: ##
   First, verify the installed Python version:
   ```
   # check Python version
   $ python3 -V
   Python 3.8.10
   $ python3 -m venv virtualenv
   $ ls
   virtualenv   
   ```
### Install ansible and Vagrant build: ###
   Then you need to install ansible 2.9.6 in virtualenv
   ```
   $ source virtualenv/bin/activate
   (virtualenv)$ python3 -m pip install --upgrade pip
   (virtualenv)$ pip install wheel
   (virtualenv)$ python3 -m pip install ansible==2.9.6
   #chech version:
   (virtualenv)$ ansible --version
   ansible 2.9.6
   (virtualenv)$ vagrant up
   ```
## Connect to VM: ##
   ```
   $ vagrant ssh ntp.edu.tentixo.com
   ```
### Checking the work of ntp servers:
   And run these commands in Rhel8:
   ```
    $ chronyc sources
    $ chronyc tracking
   ```
## About files: ##
### Vagrant files: ###
   ```
#This line is responsible for the name of the configuration and version vagrant.
Vagrant.configure("2") do |config|
  config.vm.define "ntp.edu.tentixo.com" do |config| 			
    config.vm.hostname = "ntp.edu.tentixo.com"				
    config.vm.box = "generic/rhel8"					
    config.vm.network "private_network", ip: "192.168.56.2"		
    config.vm.box_check_update = false					

  end

    config.vm.provider "virtualbox" do |vb|				 
      vb.cpus = 1							 
      vb.gui = false							 
      vb.memory = "1024"						

    end

    config.ssh.insert_key = false					
    config.vm.provision :ansible do |ansible|				
    	ansible.playbook = "playbook.yml"					
    	ansible.inventory_path = "inventory"				
    	ansible.raw_arguments = ["-vvv", "--flush-cache"
	]								 

    end

end
   ```
### Playbook.yml file: ###
   ```
   ---
- hosts: ntp										
  become: true										
  tasks:
    - name: Update Operation system							
      package:
        name: '*'
        state: latest
    - name: Copy line the chrony configuration
      lineinfile:									
        path: /etc/chrony.conf
        regexp: '{{item.regexp}}'							
        line: '{{item.line}}'								
        backrefs: yes									
      with_items:
        - {regexp: '^pool(.*)', line: 'server sth1.ntp.se \n server sth4.ntp.se' }
    - name: Restart Chrony service							
      systemd:
        name: chronyd
        state: restarted
   ```
### About inventory file: ###
   ```
    You can read more information about inventory file here:
    https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html
   ```
### About requirements.txt file: ###
   ```
   Good article about requirements.txt:
   https://blog.sedicomm.com/2021/06/29/chto-takoe-virtualenv-v-python-i-kak-ego-ispolzovat/
   ```
## Useful links
  If you have some problems, these sites will help you to solve them:<br>
  1.https://docs.ansible.com/ansible/2.9/modules/systemd_module.html<br>
  2.https://docs.ansible.com/ansible/2.8/user_guide/playbooks_best_practices.html<br>
  3.https://github.com/Karandash8/virtualbox_WSL2<br>
  4.https://stackoverflow.com/questions/40535667/ansible-failed-to-connect-to-the-host-via-ssh<br>
  5.https://www.schakko.de/2020/01/10/fixing-unprotected-key-file-when-using-ssh-or-ansible-inside-wsl/<br>
  6.https://stackoverflow.com/questions/41377375/failed-to-connect-to-host-via-ssh-on-vagrant-with-ansible-playbook<br>
