---
sidebar_position: 2
---

# Getting Started

Transform your fresh server into a `mitte` host.

## 1. Run the Setup on Your Server

SSH into your server as root and run the installer. This script downloads the latest `mitte` binary and runs the `mitte setup` command for you.

```bash
# Run this on your DEDICATED server
ssh root@your-server.com
curl -sSL https://mitte.sh/install.sh | bash
```

## 2. Add Your Public SSH Key

On your local machine, add your SSH key to the `mitte` user on the server. This authorizes you to push code.

```bash
# Run this on your LOCAL machine
cat ~/.ssh/id_rsa.pub | ssh root@your-server.com "mitte keys add my-laptop"
```

## 3. Deploy Your First App

In your local git repository, add a `mitte` remote and push!

```bash
# In your project directory
git remote add mitte mitte@your-server.com:my-awesome-app
git push mitte main
```

**That's it!** Your application is now deployed at `http://my-awesome-app.your-server.com`.

:::note
Mitte supports three deployment modes:

- **Source Code with Dockerfile**: Push your code with a `Dockerfile` and let Mitte build it automatically
- **Source Code with Buildpacks**: Push your code and let Mitte detect your language and build using Cloud Native Buildpacks
- **Pre-built Images**: Configure a Docker image and deploy it directly
  :::
