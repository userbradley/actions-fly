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
        uses: userbradley/actions-fly@${{version}}
        with:
          # Set this to your account or application token
          flyToken: ${{ secrets.FLY_ACCESS_TOKEN_DEV }}
          # name of the config file in the Repository for the application
          configFile: "dev.toml"
          # Name of the Dockerfile in the Repo.
          dockerfileName: "dev.Dockerfile"
```