# App Management

Manage the lifecycle of your applications.

```bash
# List all deployed applications
mitte apps list

# Create a new, empty application
mitte apps create <appname>

# Set a pre-built Docker image for an app
mitte apps set-image <appname> <image>

# Configure volume mounts for an app
mitte apps set-volumes <appname> /host/path:/container/path

# Configure port mappings for an app
mitte apps set-ports <appname> 8080:80

# Configure a custom command/entrypoint for an app
mitte apps set-command <appname> serve --port 8080

# Configure a custom user (UID:GID) to run the container
mitte apps set-user <appname> 1000:1000

# Deploy a pre-built image (after configuration)
mitte apps deploy-image <appname>

# Set the buildpack to use for an app
mitte apps set-buildpack <appname> <buildpack-id>

# Detect and suggest a buildpack for an application
mitte apps detect-buildpack <appname>

# Enable an application
mitte apps enable <appname>

# Disable an application
mitte apps disable <appname>

# Permanently destroy an application and all its resources
mitte apps destroy <appname>
```
