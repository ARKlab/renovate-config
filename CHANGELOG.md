# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

## [1.0.0] - 2026-10-09

### Removed

- `dotnetWorkloadRestore` is no longer enabled by default, so NuGet lock file updates no longer run a slow `dotnet workload restore`. Repositories that need SDK workloads can add it back to `postUpdateOptions` in their own config.

[Unreleased]: https://github.com/ARKlab/renovate-config/compare/1.0.0...HEAD
[1.0.0]: https://github.com/ARKlab/renovate-config/releases/tag/1.0.0
