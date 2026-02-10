# PostgreSQL Management

Manage PostgreSQL database instances for your applications.

## Basic Commands

```bash
# List all PostgreSQL instances
mitte postgres list

# Create a new PostgreSQL instance
mitte postgres create <instance-name> [--version=latest] [--database=name]

# Link a PostgreSQL instance to an app (sets DATABASE_URL)
mitte postgres link <instance-name> <app-name> [env-var-name]
```

## Backup & Restore

```bash
# Create a backup
mitte postgres backup <instance-name> <output-file>

# Restore from backup
mitte postgres restore <instance-name> <backup-file>
```

## User Management

```bash
# Create a user
mitte postgres users create <instance-name> <username> [--password=...] [--database=...]

# List users
mitte postgres users list <instance-name>

# Delete a user
mitte postgres users delete <instance-name> <username>
```
