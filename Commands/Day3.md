# Ansible Playbook Deep Dive

Concepts 
- Handlers 
- Variables 
- Template (Jinja2)
- Conditionals and Loops

## Handlers 
Event based triggers e.g. Restart th server as soon as configuration are enabled 

## Variables 
To avoid the repeation 

## Templates (Jinja2)
Config files in Ansible are generally written with the Jinja so that you can define the variables/conditions 

e.g. `nginx.conf.j2`

## Condition and Loops 
Use case:
- Conditionally install a package. 
- Install multiple packages without repeating the structure for tasks. 


