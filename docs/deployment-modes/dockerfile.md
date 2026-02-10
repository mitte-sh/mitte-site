# Deployment with Dockerfile

This is the default deployment method for Mitte. When you push your source code, Mitte looks for a `Dockerfile` in the root of your repository.

## How It Works

1. **Receives** the source code in a bare git repository.
2. **Builds** the code into a Docker image using your `Dockerfile`.
3. **Runs** the image as a new container.
4. **Routes** traffic to the new container by dynamically updating its Caddy reverse proxy via Caddy's admin API.

## Usage

Simply include a `Dockerfile` in your project root.

```bash
git push mitte main
```

Mitte will automatically trigger the build process using Docker.
