# Getting Started with Ansible

## Concepts 
1. What is ansible?
2. Setup on the Ansible (Ansible Master)
3. Setup to the Managed Nodes 
4. Create a Static Inventory 

## Ansible 
- Ansible Master 
- Target Nodes

## Install Ansible 
Install ansible with the command 
```
sudo apt update
sudo apt install ansible -y
```

Check if ansible is installed 
```
ansible --version
```

## Setup Managed Nodes 
Generate the private public key on the ansible master
```
ssh-keygen
```

Copy the public key to the host machines 
```
ssh-copy-id ajay@172.208.68.222
```

Validate if the connection is established
```
ssh ajay@172.208.68.222
```

## Ansible Static Inventory 
Create a file with name `hosts.ini`. It includes the list of the file which ansible manages. 

Here's the content of the hosts.ini file 
```
[webservers]
192.168.56.101
192.168.56.102

[dbservers]
192.168.56.103
```

## Commmands 

### Ping all remote servers to see if they are reachble
`ansible all -i hosts.ini -m ping`

### Check if you able to execute the command 
`ansible all -i hosts.ini -m command -a "uptime"`

### Run command manually
`ansible webservers -i hosts.ini -m apt -a "name=nginx state=present" --become`

### Run ansible playbook with servers defined in the hosts.ini file
`ansible-playbook -i config/hosts.ini playbooks/install_nginx.yaml`

