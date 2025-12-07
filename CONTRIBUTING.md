# Contributing to vrclog

- Japanese translation: [CONTRIBUTING.ja.md](./CONTRIBUTING.ja.md)

Thank you for your interest in contributing to vrclog! We welcome contributions from everyone. This guide will help you get started.

## Overview

**vrclog** is a GitHub organization developing open-source tools for working with VRChat log files. Our flagship repository is:

- **[vrclog-go](https://github.com/vrclog/vrclog-go)**: A Go library and CLI for parsing and monitoring VRChat logs

All vrclog tools are designed to run locally on your machine. They read VRChat log files to extract structured event data (joins, leaves, world changes, etc.) without uploading anything to external servers by default.

> **Note**: vrclog is an unofficial community project and is not affiliated with VRChat Inc.

## Ways to Contribute

There are many ways to contribute to vrclog:

### Bug Reports

Found a bug? Please [open an issue](https://github.com/vrclog/vrclog-go/issues/new) with:

- A clear description of the problem
- Steps to reproduce the issue
- Expected vs. actual behavior
- Your environment (OS, Go version, tool version)
- Relevant log snippets (see [Privacy Notice](#privacy-notice) below)

### Feature Requests

Have an idea for a new feature? We'd love to hear it! Please [open an issue](https://github.com/vrclog/vrclog-go/issues/new) describing:

- The problem you're trying to solve
- Your proposed solution
- Any alternatives you've considered

### Documentation

Documentation improvements are always welcome:

- Fix typos or clarify existing docs
- Add examples or tutorials
- Translate documentation (we maintain English and Japanese versions)

### Code Contributions

Ready to write some code? See the [Development Guide](#development-guide-go) below.

### Tests

Help us improve test coverage:

- Add tests for uncovered code paths
- Write integration tests
- Report test failures

## Development Guide (Go)

### Prerequisites

- **Go 1.22 or later** (we follow Go's N-1 support policy)
- **Git**
- A Windows machine with VRChat installed (for testing with real logs)

### Getting Started

1. Fork the repository
2. Clone your fork:
   ```bash
   git clone https://github.com/YOUR_USERNAME/vrclog-go.git
   cd vrclog-go
   ```
3. Create a branch for your changes:
   ```bash
   git checkout -b feature/your-feature-name
   ```

### Code Style

- **Format your code** with `gofmt` before committing
- Follow standard Go conventions and idioms
- Keep it simple – prefer clarity over cleverness
- Write descriptive commit messages

### Running Tests

Before submitting a PR, ensure all tests pass:

```bash
go test ./...
```

### Static Analysis (Optional but Recommended)

We recommend using `golangci-lint` for additional checks:

```bash
golangci-lint run
```

This is optional for contributors but will be run in CI.

## Issues

### Before Opening an Issue

1. Search existing issues to avoid duplicates
2. Check if the issue is related to vrclog or VRChat itself (we can only help with vrclog)

### Writing a Good Issue

- Use a clear, descriptive title
- Provide as much context as possible
- Include reproduction steps for bugs
- Attach relevant logs (with privacy considerations – see below)

## Pull Requests

### Small Changes

For small bug fixes or documentation improvements, feel free to open a PR directly.

### Large Changes

For significant changes (new features, API changes, architectural modifications):

1. **Open an issue first** to discuss the approach
2. Wait for maintainer feedback before investing significant time
3. Reference the issue in your PR

### PR Checklist

Before submitting your PR:

- [ ] Tests added or updated
- [ ] `go test ./...` passes
- [ ] Code formatted with `gofmt`
- [ ] Documentation updated (if applicable)
- [ ] Commit messages are clear and descriptive

### PR Review Process

1. A maintainer will review your PR
2. You may be asked to make changes
3. Once approved, a maintainer will merge your PR

## Translation Workflow

We maintain documentation in both English and Japanese:

- **English (`.md`)** is the source of truth
- **Japanese (`.ja.md`)** files are translations

### For Translators

- Translations may lag behind English – this is OK
- If you notice outdated translations, please open an issue or PR
- When updating English docs, you don't need to update Japanese simultaneously (but it's appreciated!)
- Ensure translations accurately convey the original meaning

## Privacy Notice

When reporting issues or sharing logs:

> **Important**: VRChat logs contain usernames, world names, and other information about yourself and others. **Never share raw logs publicly without redacting personal information.**

- Remove or redact other users' display names
- Remove or redact world instance IDs if they could identify specific sessions
- When in doubt, ask a maintainer how to share information safely

## Code of Conduct

All contributors are expected to follow our [Code of Conduct](./CODE_OF_CONDUCT.md). Please read it before participating.

## Questions?

- Open an issue for project-related questions
- Email vrclog@googlegroups.com for private inquiries

Thank you for contributing to vrclog!
