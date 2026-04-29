# Architecture

## Goals

- Keep only actively maintained Ubuntu devcontainers.
- Centralize shared shell configuration to avoid duplication.
- Preserve runtime behavior while simplifying maintenance.

## Layers

1. Base image layer
   - `base/ubuntu/Dockerfile`
   - Parameterized by `UBUNTU_VERSION` (for example, `24.04` or `26.04`).
2. Shared shell config layer
   - `shared/shell/dot-zshrc`
   - `shared/shell/starship.toml`
   - `shared/shell/key-bindings.zsh`

## Change Policy

- Add Ubuntu variant support through `UBUNTU_VERSION`, not by duplicating Dockerfiles.
- Keep shell config in `shared/shell/` and copy into the image at build time.
- Avoid committing binaries or archives to source control.
