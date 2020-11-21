This project is a simple reproducible setup of my raspberry pi using [Ansible](https://www.ansible.com/).

To run the configuration, set up your system as detailed below and then execute
```./build.sh```

# Set up your system
* Install virtualenv as described [here](https://virtualenv.pypa.io/en/latest/installation/)

* Create and activate a Python virtual environment for this project's installations
```
virtualenv --python=python3 .venv
source .venv/bin/active
```

* Install this project's Python requirements inside your virtualenv
```
pip3 install -r requirements.txt
```

* Install ansible roles using the ansible requirements file.
```
ansible-galaxy install -r requirements.yml
```

* create a new plain text inventory.ini file to replace the encrypted inventory.ini file

* add the folling line of code to define a group of hosts
```
[raspberry_pis]
```

* add this line code for each of your raspberry pis
```
XXX.XXX.X.XX ansible_user=YYYY ansible_ssh_pass=ZZZZ ansible_become_pass=ZZZZ
```
where these are your raspberry PI IP addresses and your ssh and sudo password for the PIs

* encrypt your new inventory.ini file
```
ansible-vault encrypt inventory.ini
```

* execute the playbook with the prompt for your ansible vault password to decrypt your inventory file. This command is in ```build.sh``` file
