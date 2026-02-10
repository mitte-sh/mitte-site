# Deployment with Pre-built Images

Mitte supports deploying pre-built Docker images directly, perfect for applications that are already containerized or for faster deployments.

## How It Works

1. **Receives** the git push (for triggering deployment) or a deploy command.
2. **Skips** the build process entirely.
3. **Pulls** the pre-configured Docker image.
4. **Runs** the image as a new container with custom volumes, ports, and environment variables.
5. **Routes** traffic to the new container.

## Configuration

### 1. Create and Configure Your App

```bash
# Create the app
ssh root@your-server.com "mitte apps create my-image-app"

# Set the Docker image
ssh root@your-server.com "mitte apps set-image my-image-app nginx:latest"

# Configure volumes (optional)
ssh root@your-server.com "mitte apps set-volumes my-image-app /host/path:/container/path"

# Configure ports (optional)
ssh root@your-server.com "mitte apps set-ports my-image-app 8080:80"

# Deploy the image
ssh root@your-server.com "mitte apps deploy-image my-image-app"
```

### 2. Deploy via Git Push (Alternative)

You can also trigger deployments of pre-built images using git push:

```bash
# In your project directory (even if empty)
git init
git remote add mitte mitte@your-server.com:my-image-app
git push mitte main
```

## ⚠️ Environment Variable Limitation

When using pre-built images, environment variables are applied at runtime, not during the image build process. This means:

- ✅ Environment variables will be available to your running container.
- ❌ Environment variables cannot be used during the image build phase.

If your application requires environment variables during the build process (e.g., `DATABASE_URL` for database migrations), use the **Source Code Deployment** method with a Dockerfile instead.
