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
        uses: actions/checkout@v4
      - name: Build and deploy
        uses: userbradley/actions-fly@${{version}}
        with:
          flyToken: ${{ secrets.FLY_ACCESS_TOKEN_DEV }}
```
