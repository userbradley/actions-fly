# Fly Build and Deploy actions

Simple action to Build and deploy a Docker file on Fly, using the GitHub actions runner Docker engine.

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
        uses: userbradley/actions-fly@v1.0.0
        with:
          flyToken: ${{ secrets.FLY_ACCESS_TOKEN_DEV }}
```

## Full Example

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
        uses: userbradley/actions-fly@v1.0.0
        with:
          # Set this to your account or application token
          flyToken: ${{ secrets.FLY_ACCESS_TOKEN_DEV }}
          # name of the config file in the Repository for the application
          configFile: "dev.toml"
          # Name of the Dockerfile in the Repo.
          dockerfileName: "dev.Dockerfile"
```


## Inputs

| Input Name       | Required | Default Value                                                   |
|------------------|----------|-----------------------------------------------------------------|
| `flyToken`       | `true`   | `null` - You need to provide this as a Repository or Org secret |
| `configFile`     | `false`  | `fly.toml`                                                      |
| `dockerfileName` | `false`  | `Dockerfile`                                                    |

## Example Repo

[userbradley/documentation.breadnet.co.uk](https://github.com/userbradley/documentation.breadnet.co.uk/blob/main/.github/workflows/dev.yaml)
