![GitHub Workflows](https://public-assets.andrewdyer.rocks/images/covers/github-workflows.png)

# GitHub Workflows

A collection of GitHub Actions and workflows to automate and streamline development processes.

## License

Licensed under the [MIT license](https:/opensource.org/licenses/MIT) and is free for private or commercial projects.

## Workflows

### Deploy / Docker

Validates a version and resolves the fully qualified image name for downstream jobs. This workflow does not currently deploy the image to a runtime or server.

```yaml
name: Deploy

on:
  workflow_dispatch:
    inputs:
      version:
        description: Version to deploy
        required: true
        type: string

jobs:
  resolve:
    uses: andrewdyer/github-workflows/.github/workflows/deploy-docker.yml@main
    with:
      image: ghcr.io/acme/example-api-web
      version: ${{ inputs.version }}

  deploy:
    needs: resolve
    runs-on: ubuntu-latest
    steps:
      - name: Deploy resolved image
        run: echo "Deploy ${{ needs.resolve.outputs.image }}:${{ needs.resolve.outputs.version }}"
```

### Inputs

| Input     | Required | Default | Description                               |
| --------- | -------- | ------- | ----------------------------------------- |
| `image`   | Yes      | —       | Fully qualified image name without a tag. |
| `version` | Yes      | —       | Version to deploy.                        |

### Outputs

| Output    | Description                               |
| --------- | ----------------------------------------- |
| `image`   | Fully qualified image name without a tag. |
| `version` | Version supplied by the caller.           |

### Rollback / Docker

Validates a target version and resolves the fully qualified image name for downstream rollback jobs. This workflow does not currently change a running deployment.

```yaml
name: Rollback

on:
  workflow_dispatch:
    inputs:
      version:
        description: Version to restore
        required: true
        type: string

jobs:
  resolve:
    uses: andrewdyer/github-workflows/.github/workflows/rollback-docker.yml@main
    with:
      image: ghcr.io/acme/example-api-web
      version: ${{ inputs.version }}

  rollback:
    needs: resolve
    runs-on: ubuntu-latest
    steps:
      - name: Restore resolved image
        run: echo "Restore ${{ needs.resolve.outputs.image }}:${{ needs.resolve.outputs.version }}"
```

### Inputs

| Input     | Required | Default | Description                               |
| --------- | -------- | ------- | ----------------------------------------- |
| `image`   | Yes      | —       | Fully qualified image name without a tag. |
| `version` | Yes      | —       | Version to restore.                       |

### Outputs

| Output    | Description                               |
| --------- | ----------------------------------------- |
| `image`   | Fully qualified image name without a tag. |
| `version` | Version supplied by the caller.           |
