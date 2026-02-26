## Playbooks

Playbooks are **YAML files** that define automation tasks.

### Creating a Simple Playbook

Create `nginx-playbook.yml`:

```yaml
- name: Install Nginx
  hosts: all          # all IPs in inventory
  become: true        # root user access
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present

    - name: Start Nginx
      service:
        name: nginx
        state: started
```

### Running Playbooks

Execute the playbook:
```bash
ansible-playbook -i inventory nginx-playbook.yml
```

Debug with verbose output:
```bash
ansible-playbook -v -i inventory nginx-playbook.yml
```

#### Verbosity Levels

| Flag | Output Level |
|------|-------------|
| `-v` | Basic verbose output |
| `-vv` | More detailed output |
| `-vvv` | Maximum verbosity for detailed logs |

---
