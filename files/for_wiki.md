## Create/Setting Virtualenv ##

#### 1. Check version. ####

Before you go any further, make sure you have Python, Pip, Virtualenv and that it’s available from your command line.

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

#### 2. Create a virtual environment. ####

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
> /usr/bin/python3.9 - your local pass to python3.9

> ~/environments/python3.9 - folder name with a virtual environment


> [more information about virtualenv](https://pypi.org/project/virtualenv/)

> [good cheat tool with commands for working with virtualenv](https://gist.github.com/frfahim/73c0fad6350332cef7a653bcd762f08d)

> [good article about venv, pyvenv, etc](https://stackoverflow.com/questions/41573587/what-is-the-difference-between-venv-pyvenv-pyenv-virtualenv-virtualenvwrappe)

#### 3. Active your virtual environment. ####

 To begin using the virtual environment, it needs to be activated:

```sh
source ~/environments/python3.9/bin/activate
```

#### 4. Install Ansible. ####

 Install Ansible:2.9.6 using requirements files:

```sh
pip install -r <paste pass to requirements file from DevSecOps project>
```

 You can use install Ansible:2.9.6 without using requirements file:

```sh
pip install ansible==2.9.6
```

You cat reed about install Python packages in [this article](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/).

#### 5. Deactivate. ####

If you are done working in the virtual environment for the moment, you can deactivate it:

```sh
deactivate
```
