### Step-by-Step Setup Flow

1. Install Ansible on any one of the instances (Control Node)
2. Ensure Control Node can SSH to other instances
3. Set up passwordless SSH authentication
4. Create inventory file in Control Node containing Private IPs of other instances
5. Test Ansible connectivity
6. Create a playbook (`.yml` configuration file), e.g., `nano install-node.yml` for Node.js
7. Run the playbook

---
