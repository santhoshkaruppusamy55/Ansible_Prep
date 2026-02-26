### SSH Key Configuration

#### Generating SSH Keys

Generate public and private keys in the Control Node:

```bash
ssh-keygen
```

This creates the following in `/home/ubuntu/.ssh/`:

| File | Description |
|------|-------------|
| `authorized_keys` | Stores trusted public keys |
| `id_rsa` | Private key |
| `id_rsa.pub` | Public key |

**Copy the public key:**
```bash
cat /home/ubuntu/.ssh/id_rsa.pub
```

### Configuring Target Servers

1. Login to other servers
2. Run `ssh-keygen` to create `/home/ubuntu/.ssh/` directory
3. Edit `authorized_keys` file and paste the public key from Control Node:
```bash
vim /home/ubuntu/.ssh/authorized_keys
```

Now the control node can ssh into other instances without any passwords or .pem file.
