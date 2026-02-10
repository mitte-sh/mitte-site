# Config, Domains & Logs

## Configuration (Env Vars)

Manage environment variables for a specific application. Changes take effect by restarting the app's container unless `--no-restart` is specified.

```bash
# List all environment variables for an app
mitte config list <appname>

# Set one or more environment variables
mitte config set <appname> DATABASE_URL=... SECRET_KEY=...

# Set a variable without restarting the application
mitte config set <appname> KEY=VALUE --no-restart

# Unset one or more environment variables
mitte config unset <appname> SECRET_KEY

# Bulk edit environment variables in a text editor
mitte config edit <appname>
```

## Domain Management

Manage custom domains for an application. Mitte will automatically provision SSL certificates for all domains.

```bash
# List all domains for an app
mitte domains list <appname>

# Add a domain to an app
mitte domains add <appname> www.my-awesome-app.com

# Remove a domain from an app
mitte domains remove <appname> www.my-awesome-app.com
```

## Log Management

View the logs of a running application.

```bash
# Show the most recent logs
mitte logs <appname>

# Show the last 100 log lines
mitte logs <appname> -n 100

# Follow the log output in real-time
mitte logs <appname> --follow
# or using the shorthand
mitte logs <appname> -f
```
