Perfect place to start 💯. Let’s keep it **super simple**, step-by-step, like I’m sitting next to you setting it up.

---

# 🟢 **Day 1: Getting Started with Ansible**

---

## **1. What is Ansible? (Super Simple)**

👉 Think of Ansible like a **remote control** for your servers.
Instead of logging into each server and typing commands manually, you write instructions once, and Ansible runs them everywhere.

* **Control Node** → Your laptop/server where Ansible is installed.
* **Managed Nodes** → The machines you want to control (servers, VMs, cloud instances).
* Communication happens over **SSH** (no agents needed).

---

## **2. Install Ansible (on Control Node)**

On a Linux system (Ubuntu/Debian):

```bash
sudo apt update
sudo apt install ansible -y
```

On CentOS/RHEL:

```bash
sudo yum install epel-release -y
sudo yum install ansible -y
```

Check if installed:

```bash
ansible --version
```

---

## **3. Setup Managed Nodes**

* Create 1–2 test servers (VMs on VirtualBox/VMware, cloud instances, or even WSL containers).
* Ensure you can SSH into them **without password** (using keys).

### Generate SSH key (on control node):

```bash
ssh-keygen
```

(Just press Enter through prompts).

### Copy key to managed node:

```bash
ssh-copy-id user@managed-node-ip
```

Now test:

```bash
ssh user@managed-node-ip
```

(Should log in without asking for password).

---

## **4. Create a Static Inventory File**

Inventory = **list of servers Ansible manages**.

Make a file called `hosts.ini`:

```ini
[webservers]
192.168.56.101
192.168.56.102

[dbservers]
192.168.56.103
```

👉 `[webservers]` and `[dbservers]` are groups. You can target groups or individual servers.

---

## **5. Run Ad-Hoc Commands**

Ad-hoc = quick one-liners (no playbook needed).

### Example 1: Ping all servers

```bash
ansible all -i hosts.ini -m ping
```

* `-i hosts.ini` → inventory file
* `-m ping` → use the `ping` module

Expected result:

```json
192.168.56.101 | SUCCESS => {"ping": "pong"}
```

---

### Example 2: Check uptime

```bash
ansible all -i hosts.ini -m command -a "uptime"
```

### Example 3: Install a package (on Ubuntu)

```bash
ansible webservers -i hosts.ini -m apt -a "name=nginx state=present" --become
```

### Example 4: Start a service

```bash
ansible webservers -i hosts.ini -m service -a "name=nginx state=started enabled=yes" --become
```

---

## ✅ What You Achieved on Day 1

* Installed Ansible.
* Connected control node ↔ managed nodes via SSH.
* Wrote your first **inventory file**.
* Ran **ad-hoc commands** to control remote servers.

👉 From here, tomorrow (Day 2), you’ll start writing **playbooks** (so you don’t repeat commands).

---

Do you want me to also prepare a **step-by-step demo exercise** (with exact commands + expected outputs) that you can run today on 2 test VMs, so you get instant hands-on results?
