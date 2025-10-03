# Ansible Playbook Basics

## Playbook Introduction 
- Playbook -> Instruction file -> Ansible what to do
- Playbook -> plays -> tasks -> applies to a group of servers (managed by ansible)

## Playbook structure
Refer any file under foler `playbooks`

## Run a playbook 
`ansible-playbook -i hosts.ini nginx.yml`

## Playbook Field Description 
- name: Description of the play or task.
- hosts: Which group of servers to run on (from inventory).
- become: yes: Run with sudo.
- tasks: List of actions.
- Modules example:
    - apt or yum → install packages.
    - service → start/stop services.
    - copy → copy files to remote servers.

## Deploy a web server
`ansible-playbook -i config/hosts.ini playbooks/webserver.yaml`

## Demo 
`ansible-playbook -i config/hosts.ini playbooks/install_nginx.yaml`
`ansible-playbook -i config/hosts.ini playbooks/nginx1.yaml`
`ansible-playbook -i config/hosts.ini playbooks/webserver.yaml`