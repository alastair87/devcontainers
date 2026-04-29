# Devcontainers

This repository contains Ubuntu-based development container definitions and shared shell configuration.

## Supported Images

- Ubuntu 24.04
- Ubuntu 26.04

Both variants are built from a single Dockerfile using a build argument.

## Repository Layout

- `base/ubuntu/Dockerfile`: Canonical Ubuntu image definition.
- `shared/shell/dot-zshrc`: Shared zsh configuration.
- `shared/shell/starship.toml`: Shared starship prompt configuration.
- `shared/shell/key-bindings.zsh`: Shared fzf key bindings.
- `docs/ARCHITECTURE.md`: Structure and ownership model.
- `docs/BUILD.md`: Build and run commands.

## Migration Notes

This tidy-up removed legacy directories and image definitions that are no longer maintained:

- `debian/`
- `fastbook/`
- `mamba/`
- `nodejs/`
- `nodejs-16.x/`
- `nodejs-current/`
- `nodejs-lts/`
- `nodejs-version.x/`

The old `ubuntu/Dockerfile` and `ubuntu/Dockerfile-2604` paths were replaced by `base/ubuntu/Dockerfile`.

## Quick Start

See `docs/BUILD.md` for full commands.
