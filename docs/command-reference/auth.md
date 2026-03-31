---
sidebar_position: 9
---

# Authentication

Manage application authentication via [Authelia](https://www.authelia.com/). Each app can have its own auth policy.

Mitte includes built-in authentication powered by Authelia. This lets you protect any application — even ones that don't have their own login system — with password authentication, two-factor authentication (TOTP), and single sign-on across all your apps.

## How it works

When auth is enabled for an app, Caddy intercepts every request and checks with the Authelia service whether the user is authenticated. If not, they're redirected to a login portal at `auth.<your-domain>`. Once logged in, the session is shared across all protected apps.

```
User Browser → Caddy (forward_auth) → Authelia → App Container
                       ↓ (if not authenticated)
                  Redirect to login portal
```

## Commands

```bash
# Set up the authentication service (run once)
mitte auth setup

# Re-run setup (e.g. if initial setup failed)
mitte auth setup --force

# Enable auth for an app (password only — one_factor)
mitte auth enable <appname>

# Enable auth with two-factor authentication (requires TOTP — two_factor)
mitte auth enable <appname> --two-factor

# Disable auth for an app
mitte auth disable <appname>

# Show auth status and policy for an app
mitte auth status <appname>

# Show Authelia service info and configured users
mitte auth info

# Add a user (interactive — prompts for email and password)
mitte auth add-user <username>

# Remove a user
mitte auth remove-user <username>

# List all users
mitte auth list-users
```

## Features

- **Single sign-on**: Log in once, access all protected apps.
- **Two-factor auth**: Optional TOTP support for extra security.
- **Per-app policies**: Each app can have its own auth policy — password only (`one_factor`) or password + 2FA (`two_factor`).
- **Per-app control**: Enable or disable auth for each app independently.
- **Self-hosted**: No third-party auth providers needed. All data stays on your server.
- **Login portal**: Clean, self-hosted login UI at `auth.<your-domain>`.
