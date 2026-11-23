# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added

- Updates of the APM CLI (`microsoft/apm` GitHub releases) come in their own "apm CLI" PR, apart from the other non-major updates, so `constraints.apm`, the CLI pins in workflows and the `apm_version` of `apm.lock.yaml` move together. The APM packages in `apm.yml` stay with the other updates.
- Updates of uv (`astral-sh/uv` GitHub releases and the `uv` PyPI package) come in their own "uv" PR, also for major versions, so the setup-uv pins in workflows and a `[tool.uv] required-version` in `pyproject.toml` move together. uv pinned elsewhere, such as a `ghcr.io/astral-sh/uv` Docker image, is not in the group.

### Changed

- Renovate now waits until a release is 3 days old before proposing it, for every package source, not only npm, and creates no branch before then. Releases without a release date (Docker images outside Docker Hub, Azure Pipelines tasks, git tags, digests of a branch) are not delayed. For npm, pnpm, yarn, cargo and poetry the package manager also applies the 3 days to lock file maintenance and to indirect dependencies, except on branches that also replace, pin or bump a package; where the package manager cannot enforce it, lock file maintenance is not delayed and its PR says so. A private feed that returns no release dates holds its updates until it does: check the Dependency Dashboard for updates pending on the release age. Security updates still come at once.
- NuGet updates to Swashbuckle.AspNetCore 11 are no longer proposed: it needs Microsoft.OpenApi 3, which does not work with ASP.NET Core 10. The cap goes away together with the Microsoft.OpenApi one.
- NuGet updates to MailKit 5 and MimeKit 5 are no longer proposed until NLog.MailKit supports them: with NLog.MailKit 6 the mail target fails at run time. A repository that does not use NLog.MailKit can lift the cap with an `allowedVersions` rule for these packages in its own `packageRules`.

### Fixed

- `default.json` is strict JSON again (a trailing comma is removed), so Renovate no longer needs its JSON5 fallback, which logs a warning and is planned for removal.

## [1.0.0] - 2026-10-09

### Removed

- `dotnetWorkloadRestore` is no longer enabled by default, so NuGet lock file updates no longer run a slow `dotnet workload restore`. Repositories that need SDK workloads can add it back to `postUpdateOptions` in their own config.

[Unreleased]: https://github.com/ARKlab/renovate-config/compare/1.0.0...HEAD
[1.0.0]: https://github.com/ARKlab/renovate-config/releases/tag/1.0.0
