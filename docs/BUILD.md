# Build Guide

Run commands from the repository root.

## Build Ubuntu 24.04

```bash
docker build \
  --build-arg UBUNTU_VERSION=24.04 \
  -f base/ubuntu/Dockerfile \
  -t alastair87/ubuntu:24.04 \
  .
```

## Build Ubuntu 26.04

```bash
docker build \
  --build-arg UBUNTU_VERSION=26.04 \
  -f base/ubuntu/Dockerfile \
  -t alastair87/ubuntu:26.04 \
  .
```

## Run

```bash
docker run --rm -it alastair87/ubuntu:24.04
```

Or:

```bash
docker run --rm -it alastair87/ubuntu:26.04
```

## Automated Weekly Publish

The repository workflow `.github/workflows/weekly-docker-publish.yml` publishes multi-architecture images to Docker Hub once per week and also supports manual dispatch.

- Schedule: Sunday 02:00 UTC.
- Platforms: `linux/amd64`, `linux/arm64`.
- Tags pushed:
  - `alastair87/ubuntu:24.04`
  - `alastair87/ubuntu:26.04`
  - `alastair87/ubuntu:latest` (26.04 build)

Required GitHub repository secrets:

- `DOCKERHUB_USERNAME`: Docker Hub account username.
- `DOCKERHUB_TOKEN`: Docker Hub access token with write permission.

To trigger manually from GitHub:

1. Open the Actions tab.
2. Select **Weekly Docker Publish**.
3. Click **Run workflow**.
