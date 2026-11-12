# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

## [1.1.0] - 2026-11-12

### Changed

- NuGet updates to Swashbuckle.AspNetCore 11 are no longer proposed: it needs Microsoft.OpenApi 3, which does not work with ASP.NET Core 10. The cap goes away together with the Microsoft.OpenApi one.
- NuGet updates to MailKit 5 and MimeKit 5 are no longer proposed until NLog.MailKit supports them: with NLog.MailKit 6 the mail target fails at run time. A repository that does not use NLog.MailKit can lift the cap with an `allowedVersions` rule for these packages in its own `packageRules`.

### Fixed

- `default.json` is strict JSON again (a trailing comma is removed), so Renovate no longer needs its JSON5 fallback, which logs a warning and is planned for removal.

## [1.0.0] - 2026-10-09

### Removed

- `dotnetWorkloadRestore` is no longer enabled by default, so NuGet lock file updates no longer run a slow `dotnet workload restore`. Repositories that need SDK workloads can add it back to `postUpdateOptions` in their own config.

[Unreleased]: https://github.com/ARKlab/renovate-config/compare/v1.1.0...HEAD
[1.1.0]: https://github.com/ARKlab/renovate-config/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/ARKlab/renovate-config/releases/tag/v1.0.0
