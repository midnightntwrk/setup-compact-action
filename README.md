# Setup Compact Action

A GitHub Action to install and cache the Midnight Compact compiler for use in CI/CD workflows.

## Features

- 🚀 **Fast installation** with intelligent caching
- 📦 **Version pinning** support (or use latest)

## Usage

### Basic Usage

```yaml
- name: Setup Compact Compiler
  uses: midnightntwrk/setup-compact-action@v1
```

### Specify Version

```yaml
- name: Setup Compact Compiler
  uses: midnightntwrk/setup-compact-action@v1
  with:
    compact-version: '0.26.0'
```

### Complete Example

```yaml
name: Build with Compact

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Compact Compiler
        uses: midnightntwrk/setup-compact-action@v1
        with:
          compact-version: '0.26.0'

      - name: Compile Compact code
        run: |
          compact compile --version
          # Your build commands here
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `compact-version` | Version of Compact compiler to install (e.g., `0.26.0` or `latest`) | No | `latest` |
| `cache-enabled` | Enable caching of the Compact installation | No | `true` |

## Outputs

| Output | Description |
|--------|-------------|
| `compact-version` | The installed version of Compact compiler |
| `cache-hit` | Whether the cache was hit (`true` or `false`) |

## Caching Strategy

The action uses GitHub Actions cache to store the Compact compiler binaries. The cache key is based on:
- Compact version
- Runner OS
- Runner architecture

This ensures fast subsequent runs while maintaining version accuracy across different platforms.

## Performance

With caching enabled:
- **First run**: ~30-60 seconds (downloads and installs)
- **Cached runs**: ~2-5 seconds (restores from cache)

---

### LICENSE

Apache 2.0.

### README.md

Provides a brief description for users and developers who want to understand the purpose, setup, and usage of the repository.

### SECURITY.md

Provides a brief description of the Midnight Foundation's security policy and how to properly disclose security issues.

### CONTRIBUTING.md

Provides guidelines for how people can contribute to the Midnight project.

### CODEOWNERS

Defines repository ownership rules.

### ISSUE_TEMPLATE

Provides templates for reporting various types of issues, such as: bug report, documentation improvement and feature request.

### PULL_REQUEST_TEMPLATE

Provides a template for a pull request.

### CLA Assistant

The Midnight Foundation appreciates contributions, and like many other open source projects asks contributors to sign a contributor
License Agreement before accepting contributions. We use CLA assistant (https://github.com/cla-assistant/cla-assistant) to streamline the CLA
signing process, enabling contributors to sign our CLAs directly within a GitHub pull request.

### Dependabot

The Midnight Foundation uses GitHub Dependabot feature to keep our projects dependencies up-to-date and address potential security vulnerabilities.

### Checkmarx

The Midnight Foundation uses Checkmarx for application security (AppSec) to identify and fix security vulnerabilities.
All repositories are scanned with Checkmarx's suite of tools including: Static Application Security Testing (SAST), Infrastructure as Code (IaC), Software Composition Analysis (SCA), API Security, Container Security and Supply Chain Scans (SCS).

