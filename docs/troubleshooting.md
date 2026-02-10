# Troubleshooting

Common issues and their solutions.

## Caddy "Connection Refused" Errors After Docker Restart

If you see errors like `dial tcp 127.0.0.1:33188: connect: connection refused` in Caddy logs after Docker restarts, it's usually because containers got new random ports.

### Immediate Fix

```bash
# Fix all broken routes
sudo mitte fix-routes

# Or restart a specific app
sudo mitte apps restart <appname>
```

### Automatic Prevention

Mitte includes a container watcher service that automatically detects port changes.

```bash
# Check watcher status
sudo mitte watcher status

# Restart the watcher
sudo mitte watcher restart

# View watcher logs
sudo mitte watcher logs
```

## Buildpack Issues with Docker 29.x+

If you encounter Docker API version errors with buildpacks, ensure you have pack CLI v0.39.0+ installed.

```bash
# The setup command installs the correct version automatically
sudo mitte setup
```
