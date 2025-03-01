# Docker Tag Exists Action

A GitHub Action to check if a Docker image/tag exists in Docker Hub.
Break the build if the image/tag does not exist.

## Inputs

| Input | Description | Required |
|-------|-------------|----------|
| `name-and-tag` | Docker image name with tag (e.g. `nginx:1.21.1`) | Yes |
| `dockerhub-username` | DockerHub username | Yes |
| `dockerhub-password` | DockerHub password | Yes |

## Outputs

No output, just breaks the build if the image/tag does not exist.

## Usage Example

```yaml

    (...)
      - name: Check if Docker image exists
        uses: your-username/docker-tag-exists@v1
        id: check_image
        with:
          name-and-tag: nginx:latest
          dockerhub-username: ${{ secrets.DOCKERHUB_USERNAME }}
          dockerhub-password: ${{ secrets.DOCKERHUB_PASSWORD }}
    (...)  

```
