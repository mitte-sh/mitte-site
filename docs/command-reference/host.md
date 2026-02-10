# Host & Project Management

Utility commands for setting up the Mitte host and local project remotes.

## Host Setup

```bash
# Initialize the Mitte host (run on the server)
# This is handled automatically by the install script.
mitte setup
```

## Local Remote Setup

```bash
# Add a git remote to your local project (run on your local machine)
# Replaces 'git remote add ...'
mitte remote --host your-server.com --app my-awesome-app
```
