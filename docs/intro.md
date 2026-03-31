---
sidebar_position: 1
---

# Introduction

**Mitte** is a personal PaaS (Platform-as-a-Service) implemented in a single, modern Go binary. It allows you to transform any server into your own private cloud deployment platform.

Using the power of Docker, Git, and Caddy, `mitte` provides a simple, self-hosted deployment workflow for any application. Deploy from source code using `git push` (with automatic building via Dockerfiles) or deploy pre-built Docker images directly for maximum flexibility and speed.

## ✨ Features

- 🚀 **Git Push to Deploy**: The classic Heroku workflow you know and love.
- 📦 **Single Go Binary**: Incredibly easy to install and manage. No complex dependency chains.
- 🔒 **Automatic HTTPS**: Caddy provides free, managed SSL certificates for all your apps, out-of-the-box.
- 🏗️ **Dockerfile Support**: Automatically builds your application using your existing `Dockerfile`.
- 📦 **Buildpack Support**: Deploy applications without Dockerfiles using Cloud Native Buildpacks (CNB) for automatic language detection and building.
- 🐳 **Pre-built Image Support**: Deploy any Docker image directly without building from source code.
- ⚙️ **Comprehensive CLI**: A powerful, easy-to-use command-line interface for managing the full lifecycle of your apps: configuration, domains, logs, and more.
- 🛡️ **Secure by Design**: Runs operations through a dedicated, unprivileged `mitte` user on the host.
- 🗄️ **MariaDB Support**: Built-in MariaDB database service with health checks, backup/restore, and custom configuration support.
- 🐘 **PostgreSQL Support**: Built-in PostgreSQL database service with health checks, backup/restore, and user management.
- 🔄 **Automatic Route Recovery**: Container watcher service automatically fixes Caddy routes after Docker restarts.
- 🛠️ **Route Management Tools**: Commands to manually fix broken routes and manage the watcher service.
- 🔐 **Application Authentication**: Protect apps with Authelia — password, 2FA, SSO across all your apps.
