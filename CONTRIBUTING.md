# Contributing to vrclog

- Japanese translation: [CONTRIBUTING.ja.md](./CONTRIBUTING.ja.md)

Thank you for your interest in contributing to vrclog! We welcome contributions from everyone. This guide will help you get started.

## Overview

**vrclog** is a GitHub organization developing open-source tools for working with VRChat log files. Our repositories include:

- **[vrclog-go](https://github.com/vrclog/vrclog-go)**: A Go library and CLI for parsing and monitoring VRChat logs
- **[vrclog-companion](https://github.com/vrclog/vrclog-companion)**: A log watcher with SQLite persistence, Web UI, and Discord notifications

All vrclog tools are designed to run locally on your machine. They read VRChat log files to extract structured event data (joins, leaves, world changes, etc.) without uploading anything to external servers by default.

> **Note**: vrclog is an unofficial community project and is not affiliated with VRChat Inc.

## Ways to Contribute

There are many ways to contribute to vrclog:

### Bug Reports

Found a bug? Please open an issue in the relevant repository:

- [vrclog-go Issues](https://github.com/vrclog/vrclog-go/issues/new)
- [vrclog-companion Issues](https://github.com/vrclog/vrclog-companion/issues/new)

Include:
- A clear description of the problem
- Steps to reproduce the issue
- Expected vs. actual behavior
- Your environment (OS, Go version, tool version)
- Relevant log snippets (see [Privacy Notice](#privacy-notice) below)

### Feature Requests

Have an idea for a new feature? We'd love to hear it! Please open an issue in the relevant repository describing:

- The problem you're trying to solve
- Your proposed solution
- Any alternatives you've considered

### Documentation

Documentation improvements are always welcome:

- Fix typos or clarify existing docs
- Add examples or tutorials
- Translate documentation (we maintain English and Japanese versions)

### Code Contributions

Ready to write some code? See the [Development Guide](#development-guide) below.

### Tests

Help us improve test coverage:

- Add tests for uncovered code paths
- Write integration tests
- Report test failures

## Good First Issues

New to vrclog or open source? Look for issues labeled `good first issue`:

- [vrclog-go Good First Issues](https://github.com/vrclog/vrclog-go/labels/good%20first%20issue)
- [vrclog-companion Good First Issues](https://github.com/vrclog/vrclog-companion/labels/good%20first%20issue)

These issues are:
- Small and well-defined (typically 2-4 hours of work)
- Often focused on tests or documentation
- Great for learning the codebase

## Development Guide

### vrclog-go

#### Prerequisites

- **Go 1.23 or later** (required for `iter.Seq2` iterator support)
- **Git**
- A Windows machine with VRChat installed (for testing with real logs)

#### Getting Started

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

#### Code Style

- **Format your code** with `gofmt` before committing
- Follow standard Go conventions and idioms
- Keep it simple – prefer clarity over cleverness
- Write descriptive commit messages

#### Running Tests

```bash
go test ./...
```

#### Static Analysis (Optional but Recommended)

```bash
golangci-lint run
```

### vrclog-companion

#### Prerequisites

- **Go 1.25 or later** (backend)
- **Node.js 20 or later** (frontend/Web UI)
- **Git**
- A Windows machine with VRChat installed (for testing with real logs)

#### Getting Started

1. Fork the repository
2. Clone your fork:
   ```bash
   git clone https://github.com/YOUR_USERNAME/vrclog-companion.git
   cd vrclog-companion
   ```
3. Create a branch for your changes:
   ```bash
   git checkout -b feature/your-feature-name
   ```

#### Backend Development

```bash
# Build and run
go build -o vrclog ./cmd/vrclog
./vrclog

# Run tests
go test ./...
```

#### Frontend Development (Web UI)

```bash
# Install dependencies
cd web
npm install

# Start development server
npm run dev

# Lint and format
npm run lint
npm run format

# Build for production
npm run build
```

The frontend development server connects to the backend API at `http://127.0.0.1:8080` by default.

## Response Times

vrclog is maintained by volunteers. Please understand that:

- **Issues**: We aim to respond within 1 week, but it may take longer
- **Pull Requests**: We aim to start review within 1-2 weeks
- **Complex issues**: May take longer to investigate

We appreciate your patience!

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

- [ ] Tests added or updated (if applicable)
- [ ] Code passes all tests
- [ ] Code formatted and linted
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
