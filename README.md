# This project
This repository exists solely to clone some Docker images (namely [``tonistiigi/binfmt``](https://hub.docker.com/r/tonistiigi/binfmt) and [``moby/buildkit``](https://hub.docker.com/r/moby/buildkit)) from the **Docker Hub container registry** to **GitHub container registry** (**GitHub Packages**), in order to be used in my own **GitHub Actions** workflows that use [Buildkit](https://github.com/moby/buildkit), avoiding exhausting the quota from Docker Hub. You may use them, too.

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
