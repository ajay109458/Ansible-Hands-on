# Advanced Playbook Features 

## Concepts 
- Blocks for error handling
- Tags for running specific part of the playbook
- Delegation to run a specific part on different host. 
- Async and poll for the long running operations 


## Block
Block allow a group of tasks to run together. 

If something fails - `rescue` or `always`


## Tags 

Run task with the specific tag 
`ansible-playbook -i config/hosts.ini nginx_tags.yaml --tags install`

Skip task with the specific tag 
`ansible-playbook -i hosts.ini nginx_tags.yml --tags config`

## Delegate 
Run a specific tasks on the on a separate server

```
- name: Run task on only one node
  hosts: webservers
  tasks:
    - name: Print message only once
      debug:
        msg: "This runs only on control node"
      run_once: true
      delegate_to: localhost
```

## Async & Poll
For long running operations 
- Package updates 
- DB migration 
- big file transfer 


```
- name: Long running update
  hosts: webservers
  tasks:
    - name: Run apt upgrade in background
      apt:
        upgrade: dist
      async: 300
      poll: 10
```