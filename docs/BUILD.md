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
