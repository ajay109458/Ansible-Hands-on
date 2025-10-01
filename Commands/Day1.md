# Ping all remote servers to see if they are reachble 
ansible all -i hosts.ini -m ping

# Check if you able to execute the command 
ansible all -i hosts.ini -m command -a "uptime"

# Run command manually
ansible webservers -i hosts.ini -m apt -a "name=nginx state=present" --become

# Run ansible playbook with servers defined in the hosts.ini file
ansible-playbook -i config/hosts.ini playbooks/install_nginx.yaml

