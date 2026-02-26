### Control Node


The **Control Node** is the central system where Ansible is installed and from which all automation tasks are executed.

- Ansible installed
- Must have **SSH access** to all managed nodes

---

## Architecture

```
         Control Node(Ansible Installed)
        /      |      \
      EC2     EC2     EC2
  (Managed) (Managed) (Managed)
```
