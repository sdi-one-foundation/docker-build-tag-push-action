# docker-build-tag-push-action
A composite Github Action for our standard Docker build/tag/push workflow steps

Example main-push.yaml that uses this action:

```yaml
name: MainPush

on:
  push:
    branches:
      - main
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Docker Build/Tag/Push
        uses: sdi-one-foundation/docker-build-tag-push-action@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1
          ecr-repository: ${{ github.event.repository.name }}
```
