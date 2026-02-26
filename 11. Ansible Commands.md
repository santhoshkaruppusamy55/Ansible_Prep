## Ansible Commands

### Adhoc Commands vs Playbooks

| | Ansible Adhoc Commands | Ansible Playbook |
|---|---|---|
| **Use** | Used for one or two commands | Used for multiple commands to execute |
| **Format** | Single line CLI command | YAML file |
| **Best For** | Quick tasks / testing | Automation and complex workflows |

### Adhoc Command Examples

Execute a shell command on **all hosts**:
```bash
ansible -i inventory all -m "shell" -a "touch devopsclass"
```
> This creates a file named `devopsclass` on all target instances.

Execute command on a **specific group**:
```bash
ansible -i inventory webservers -m "shell" -a "df"
```

---
