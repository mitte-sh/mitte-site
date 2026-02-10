# Deployment with Buildpacks

Mitte supports deploying applications using Cloud Native Buildpacks (CNB), which automatically detect your application's language and framework, eliminating the need for a `Dockerfile`.

## How It Works

1. **Receives** the source code in a bare git repository.
2. **Detects** the application language and framework automatically.
3. **Builds** the application using Cloud Native Buildpacks (CNB) without requiring a `Dockerfile`.
4. **Runs** the built image as a new container.
5. **Routes** traffic to the new container.

## Configuration

### 1. Configure Buildpack for Your App

```bash
# Create the app
ssh root@your-server.com "mitte apps create my-buildpack-app"

# Set a specific buildpack (optional - auto-detection will be used if not set)
ssh root@your-server.com "mitte apps set-buildpack my-buildpack-app paketobuildpacks/nodejs"

# Configure environment variables (optional)
ssh root@your-server.com "mitte config set my-buildpack-app NODE_ENV=production"
```

### 2. Deploy via Git Push

```bash
# In your project directory
git remote add mitte mitte@your-server.com:my-buildpack-app
git push mitte main
```

## Supported Languages

Mitte can automatically detect and build applications in:

- **Node.js** (`package.json`)
- **Python** (`requirements.txt`, `Pipfile`, `pyproject.toml`)
- **Go** (`go.mod`, `go.sum`, `main.go`)
- **Java** (`pom.xml`, `build.gradle`, `build.gradle.kts`)
- **.NET** (`*.csproj`, `*.fsproj`, `project.json`)
- **Ruby** (`Gemfile`)
- **PHP** (`composer.json`)

:::info
Buildpack support requires the `pack` CLI (v0.39.0 or later) to be installed on your server. The `mitte setup` command automatically installs the latest compatible version.
:::
