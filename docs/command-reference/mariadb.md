# MariaDB Management

Manage MariaDB database instances for your applications.

## Basic Commands

```bash
# List all MariaDB instances
mitte mariadb list

# Create a new MariaDB instance
mitte mariadb create <instance-name> [--version=latest] [--database=name]

# Link a MariaDB instance to an app (sets DATABASE_URL)
mitte mariadb link <instance-name> <app-name> [env-var-name]
```

## Backup & Restore

```bash
# Create a backup
mitte mariadb backup <instance-name> <output-file>

# Restore from backup
mitte mariadb restore <instance-name> <backup-file>
```

## Connection Pooling

Mitte provides advanced connection pooling optimization.

```bash
# Show connection statistics
mitte mariadb connections stats <instance-name>

# Analyze connection usage and get recommendations
mitte mariadb connections analyze <instance-name>

# Apply a pooling preset
mitte mariadb connections apply <instance-name> --pooling-preset=high-traffic --restart
```

### Presets
- **small**: 100 connections, 8 thread cache, 256M buffer pool (development)
- **medium**: 200 connections, 50 thread cache, 1G buffer pool (standard production)
- **large**: 300 connections, 75 thread cache, 2G buffer pool (high-concurrency)
- **high-traffic**: 500 connections, 100 thread cache, 4G buffer pool (enterprise)

## Upgrades

```bash
# Check upgrade status
mitte mariadb upgrade check <instance-name>

# Perform upgrade to a specific version
mitte mariadb upgrade perform <instance-name> --to-version=10.11
```
