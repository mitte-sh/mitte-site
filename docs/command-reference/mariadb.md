# MariaDB Management

Manage MariaDB database instances for your applications.

## Basic Commands

```bash
# List all MariaDB instances
mitte mariadb list

# Create a new MariaDB instance
mitte mariadb create <instance-name> [--version=latest] [--database=name] [--user=username] [--password=password] [--config-file=path] [--data-dir=path] [--max-connections=N] [--thread-cache-size=N] [--table-open-cache=N] [--innodb-buffer-pool-size=SIZE] [--query-cache-size=SIZE] [--pooling-preset=PRESET]

# Example: Create a MariaDB instance with version 10.11 and initial database 'myapp'
mitte mariadb create mydb --version=10.11 --database=myapp

# Example: Create a MariaDB instance with a custom user
mitte mariadb create mydb --user=myuser --database=myapp

# Example: Create a MariaDB instance with custom configuration
mitte mariadb create mydb --config-file=/path/to/my-config.cnf

# Example: Create a MariaDB instance with a custom host data directory
mitte mariadb create mydb --data-dir=/docker/joplindb

# Example: Create with connection pooling preset
mitte mariadb create mydb --pooling-preset=high-traffic --version=10.11

# Link a MariaDB instance to an app (sets DATABASE_URL)
mitte mariadb link <instance-name> <app-name> [env-var-name]

# Permanently destroy a MariaDB instance and its data
mitte mariadb destroy <instance-name>
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

# Generate optimized configuration based on current usage or preset
mitte mariadb connections optimize <instance-name> [--preset=small|medium|large|high-traffic]

# Apply a pooling preset
mitte mariadb connections apply <instance-name> --pooling-preset=high-traffic --restart

# Example: Apply pooling configuration with flags
mitte mariadb connections apply <instance-name> --max-connections=500 --thread-cache-size=100 --innodb-buffer-pool-size=2G --restart
```

### Presets
- **small**: 100 connections, 8 thread cache, 256M buffer pool (development)
- **medium**: 200 connections, 50 thread cache, 1G buffer pool (standard production)
- **large**: 300 connections, 75 thread cache, 2G buffer pool (high-concurrency)
- **high-traffic**: 500 connections, 100 thread cache, 4G buffer pool (enterprise)

## User Management

```bash
# Create a database user
mitte mariadb users create <instance-name> <username> [--password=...] [--database=...] [--privileges=...]

# Delete a database user
mitte mariadb users delete <instance-name> <username>

# List all database users
mitte mariadb users list <instance-name>

# Example: Create a read-only user
mitte mariadb users create mydb readonly --database=mydata --privileges=SELECT

# Example: Create a user with full privileges
mitte mariadb users create mydb appuser --database="*" --privileges="ALL PRIVILEGES"
```

## Upgrades

```bash
# Check upgrade status
mitte mariadb upgrade check <instance-name>

# Perform upgrade to a specific version
mitte mariadb upgrade perform <instance-name> --to-version=10.11

# Example: Dry run upgrade to latest version
mitte mariadb upgrade perform <instance-name> --to-version=latest --dry-run
```
