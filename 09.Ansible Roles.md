## Ansible Roles

Ansible Roles help **structure playbooks efficiently** for complex tasks. When a playbook file becomes too large and complex with many tasks, roles provide better organization.

### Creating Roles

1. Create a roles folder:
```bash
mkdir roles
cd roles
```

2. Initialize a new role (e.g., "Kubernetes"):
```bash
ansible-galaxy role init Kubernetes
```

3. A folder named `Kubernetes` will be created with the following structure:

### Role Folder Structure

| Folder | Purpose |
|--------|---------|
| `tasks/` | Main logic and task definitions |
| `handlers/` | Service restart handlers |
| `defaults/` | Default variables (lower priority) |
| `vars/` | High priority variables |
| `templates/` | Jinja2 templates |
| `files/` | Static files |
| `meta/` | Role dependencies |
| `tests/` | Test files |
| `readme` | Documentation |

### Project Folder Structure

```
Project/
├── inventory.ini
├── site.yml
└── roles/
    └── Kubernetes/
        ├── tasks/
        ├── handlers/
        ├── defaults/
        ├── vars/
        ├── templates/
        ├── files/
        └── meta/
```

### Implementing Roles

**Step 1: Write Tasks**

Create `roles/Kubernetes/tasks/main.yml`:

```yaml
- name: Install Nginx
  apt:
    name: nginx
    state: present
  notify: Restart nginx
```

**Step 2: Write Handler**

Create `roles/Kubernetes/handlers/main.yml`:

```yaml
- name: Restart nginx
  service:
    name: nginx
    state: restarted
```

**Step 3: Create Main Playbook**

Create `site.yml` in the root of the project:

```yaml
- name: Install web server
  hosts: all
  become: yes
  roles:
    - kubernetes
```

**Step 4: Run the Playbook**

```bash
ansible-playbook -i inventory.ini site.yml
```

---
