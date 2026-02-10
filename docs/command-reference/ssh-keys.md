# Access Management (SSH Keys)

Manage the public SSH keys that are authorized to deploy applications.

```bash
# Add a new SSH key from stdin
cat ~/.ssh/id_rsa.pub | ssh root@your-server.com "mitte keys add <key-name>"

# List all authorized SSH keys
ssh root@your-server.com "mitte keys list"

# Remove an SSH key by its name
ssh root@your-server.com "mitte keys remove <key-name>"
```
