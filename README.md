# buildkit and binfmt Docker images
This repository exists solely to clone some Docker images (namely [``moby/buildkit``](https://hub.docker.com/r/moby/buildkit) and [``tonistiigi/binfmt``](https://hub.docker.com/r/tonistiigi/binfmt)) from the **Docker Hub container registry** to **GitHub Artifact registry** (**GitHub Packages**) using [crane](https://github.com/google/go-containerregistry/blob/main/cmd/crane/doc/crane.md), in order to be used in my own **GitHub Actions** workflows that use [Buildkit](https://github.com/moby/buildkit), avoiding exhausting the quota from Docker Hub. You may use it on your workflows, too.

Images are built weekly.

[![docker image to ghcr](https://github.com/amitie10g/buildkit-binfmt/actions/workflows/to-ghcr.yaml/badge.svg)](https://github.com/amitie10g/buildkit-binfmt/actions/workflows/to-ghcr.yaml)

# Usage
```yaml
jobs:
  build:
  steps:
  - name: Set up QEMU
      uses: docker/setup-qemu-action@v3
      with:
        image: ghcr.io/amitie10g/binfmt:latest
    - name: Set up Docker Buildx
      uses: docker/setup-buildx-action@v3
      with:
        driver-opts: |
          image=ghcr.io/amitie10g/buildkit:master
```
