## Deployment/Scaling a web applicatin 
Take hypothetical example of High Traffic Website which recipie you can cook based on the integredients. 
- 100 Web servers 
- 10 DB

### Part 1 - Provision Infrastructure 
Spin up 100 web + 10 DB servers 

#### Azure Native Provisioning
Azure - ARM templates (via Ev2 or directly), Biceps, Terraform, Azure CLI/PS

In this step, you generally do -> Create 100 VMs with ARM/Bicep → auto load-balanced behind Azure Load Balancer.

---

#### Configuration and Deployment 
Once servers exist → kaise configure karein?

##### **Azure Native Configuration Tools**
- Azure vM Extensions, Azure Automation State Configuration (DSC), Azure DevOps + Release Pipeline, Ev2 

---

##### **Bare Metal / Hybrid / Custom Clouds → Enter Ansible**

When infra is not purely Azure (like: hybrid, on-prem, multi-cloud), config needs to be portable.

Here Ansible shines:

* Same playbook → can configure **Azure VMs, AWS, GCP, or bare-metal servers**.
* Modules for **Nginx, MySQL, Docker, Kubernetes, Security, Monitoring**.
* Roles and inventories to manage **100 web + 10 DB servers** easily.
