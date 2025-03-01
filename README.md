# Docker Tag Exists Action

A GitHub Action to check if a Docker image/tag exists in Docker Hub.

## Inputs

| Input | Description | Required |
|-------|-------------|----------|
| `name-and-tag` | Docker image name with tag (e.g. `nginx:1.21.1`) | Yes |
| `dockerhub-username` | DockerHub username | Yes |
| `dockerhub-password` | DockerHub password | Yes |

## Outputs

| Output | Description |
|--------|-------------|
| `exists` | Boolean value (`true`/`false`) indicating if the image/tag exists |

## Usage Example

```yaml
name: Check Docker Image

on:
  workflow_dispatch:
    inputs:
      image:
        description: 'Docker image to check'
        required: true
        default: 'nginx:latest'

jobs:
  check-image:
    runs-on: ubuntu-latest
    steps:
      - name: Check if Docker image exists
        uses: your-username/docker-tag-exists@v1
        id: check_image
        with:
          name-and-tag: ${{ github.event.inputs.image }}
          dockerhub-username: ${{ secrets.DOCKERHUB_USERNAME }}
          dockerhub-password: ${{ secrets.DOCKERHUB_PASSWORD }}
      
      - name: Use the output
        run: |
          if [ "${{ steps.check_image.outputs.exists }}" == "true" ]; then
            echo "Image exists!"
          else
            echo "Image does not exist!"
          fi
```
