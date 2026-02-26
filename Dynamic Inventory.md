## Dynamic Inventory

**Dynamic Inventory** allows Ansible to automatically fetch the list of servers from an external source (like AWS) instead of using a manually written static file.

### Use Case

When an EC2 instance is shut down and Auto Scaling creates a new EC2 instance, Dynamic Inventory will:

1. Connect to AWS API
2. Get EC2 instance list
3. Filter by tag
4. Automatically update the inventory (if configured)

### Dynamic Inventory Project Structure

```
ansible-project/
├── aws-ec2.yml
├── site.yml
└── roles/
    └── nginx/
```

### AWS Dynamic Inventory Configuration

Create `aws-ec2.yml`:

```yaml
plugin: amazon.aws.aws_ec2
region:
  - ap-south-1
filters:
  tag:Role: web
```

### Running Playbook with Dynamic Inventory

```bash
ansible-playbook site.yml -i aws-ec2.yml
```

> The `-i` flag automatically fetches IPs and runs the playbook **without a static inventory file**.

### Prerequisites for Dynamic Inventory

Install required collections and dependencies on Control Node:

```bash
ansible-galaxy collection install amazon.aws
pip install boto3 botocore
```

---
