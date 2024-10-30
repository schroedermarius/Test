# Test

## Environment Pipeline

This repository contains a pipeline that consumes secrets from different environments and outputs the chosen environment via markdown.

### Pipeline Configuration

The pipeline is defined in the `.github/workflows/environment-pipeline.yml` file. Below is an example of the pipeline configuration:

```yaml
name: Environment Pipeline

on:
  push:
    branches:
      - main

jobs:
  environment-pipeline:
    runs-on: ubuntu-latest

    env:
      ENV_SECRET: ${{ secrets.ENV_SECRET }}

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up environment
        run: echo "Setting up environment"

      - name: Consume secret
        run: echo "Consuming secret: $ENV_SECRET"

      - name: Output environment
        run: echo "## Chosen Environment: ${{ github.event.inputs.environment }}" > output.md
```
