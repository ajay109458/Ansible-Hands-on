# Roles 

Topics 
- Role Definition 
- Role Structure 
- Create a Role 
- Use role in a playbook 

## Role Definition 
- A role is a way to organize playbooks into reusable building blocks.
- Instead of one big messy nginx.yaml, you can create a role like roles/nginx/ with its own 
  - tasks
  - handlers
  - templates
  - files
  - vars.
- role = small Ansible project

## Role Structure 
roles/
  nginx/
    tasks/         # playbook tasks
    handlers/      # handlers
    templates/     # Jinja2 templates
    files/         # static files
    vars/          # variables with default values
    meta/          # role metadata (dependencies)
 

## Create  arole 
ansible-galaxy init roles/nginx --force

## Role a playbook with role 
ansible-playbook -i config/hosts.ini playbooks/nginx4_roles.yaml

## Install a role from the Ansible Galaxy 
(Github for Ansible Role / NPM / MAVN / NuGet)

ansible-galaxy install geerlingguy.nginx


ansible-playbook -i config/hosts.ini playbooks/nginx4_roles1.yaml