# GitHub Action: Fly Build and Deploy

Builds a docker image and deploys it on fly

## Quickstart

```yaml
name: Build and Deploy
on:
  push:
    branches:
      - main
jobs:
  site:
    runs-on: ubuntu-latest
    name: Build and Deploy
    steps:
      - name: Git Clone
        uses: actions/checkout@v3
      - name: Build and deploy
        uses: userbradley/actions-fly@v1.1.0
        with:
          flyToken: ${{ secrets.FLY_ACCESS_TOKEN_DEV }}
```
## Inputs

| Name | Description | Required | Default Value |
|------|-------------|----------|---------------|
| `dockerfileName` | Name of the Dockerfile to build from | `false` | `Dockerfile` |
| `flyToken` | Fly application token | `true` | `Null` |
| `configFile` | Name of the Config File to deploy with | `false` | `fly.toml` |

## Examples

### Full Example

```yaml
name: Build and Deploy
on:
  push:
    branches:
      - main
jobs:
  site:
    runs-on: ubuntu-latest
    name: Build and Deploy
    steps:
      - name: Git Clone
        uses: actions/checkout@v3
      - name: Build and deploy
        uses: userbradley/actions-fly@v1.1.0
        with:
          # Set this to your account or application token
          flyToken: ${{ secrets.FLY_ACCESS_TOKEN_DEV }}
          # name of the config file in the Repository for the application
          configFile: "dev.toml"
          # Name of the Dockerfile in the Repo.
          dockerfileName: "dev.Dockerfile"
```

---
Built with ❤️
