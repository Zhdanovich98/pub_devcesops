## Helper  ##

#### 1. No module named 'ansible' ####
```
Traceback (most recent call last):
  File "/usr/bin/ansible-playbook", line 34, in <module>
    from ansible import context
ModuleNotFoundError: No module named 'ansible'
```
 If you get this error, you didnt install ansible in virtual env. You should install ansible with requirements.txt:

```sh
pip install -r ./files/requirements.txt
```

 Or install ansible without requirements.txt:

```sh
pip install ansible==2.9.6
```

#### 2. FileNotFoundError: python ####
```
FileNotFoundError: [Errno 2] No such file or directory: '/usr/bin/python3.7'
```
If you get this error, you indicated python version, which not found on your host machine. Or you indicated false path to python<version>.
```sh
Please, check path to you python.
```

#### 3. Ssh error ####

```
fatal: [ntp.edu.tentixo.com]: UNREACHABLE! => {"changed": false, "msg": "Failed to connect to the host via ssh: ssh: connect to host 172.16.1.30 port 22: Connection timed out", "unreachable": true}
```

If you get this error, you should check inventory file from ansible. Ansible uses the relative path to the private_ssh key that vagrant created. Path to inventory file: <project directory>/files/ansible/inventory . You should
compare path in inventory file with path to ssh from vagrant. You can see the path to ssh from the command using Vagrant:

```sh
vagrant ssh-config
```
Also you should check content in ansible_ssh_port, ansible_user and the IP adress in ansible_host.
