# Contributing to vrclog

- Japanese translation: [CONTRIBUTING.ja.md](./CONTRIBUTING.ja.md)

Thank you for your interest in contributing to vrclog! We welcome contributions from everyone. This guide will help you get started.

## Overview

**vrclog** is a GitHub organization developing open-source tools for working with VRChat log files. Our repositories include:

- **[vrclog-go](https://github.com/vrclog/vrclog-go)**: The core Go library and CLI for reading, following, and parsing VRChat logs into canonical events and observations
- **[vrclog-adapters](https://github.com/vrclog/vrclog-adapters)**: Compile-time adapters for log formats emitted by community VRChat projects such as YamaPlayer and iwaSync3
- **[vrclog-companion](https://github.com/vrclog/vrclog-companion)**: A local resident application with SQLite persistence, a Web UI, an HTTP API, and Discord notifications

All vrclog tools are designed to run locally on your machine. They read VRChat log files to extract structured event data (joins, leaves, world changes, media URLs, etc.) without uploading anything to external servers by default.

> **Note**: vrclog is an unofficial community project and is not affiliated with VRChat Inc.

## Ways to Contribute

There are many ways to contribute to vrclog:

### Bug Reports

Found a bug? Please open an issue in the relevant repository:

- [vrclog-go Issues](https://github.com/vrclog/vrclog-go/issues/new)
- [vrclog-adapters Issues](https://github.com/vrclog/vrclog-adapters/issues/new)
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

### Adapters

Have a community VRChat project (a world asset, video player, or similar) that writes its own log lines? See [Writing a New Adapter](#writing-a-new-adapter) in the `vrclog-adapters` development guide below.

### Tests

Help us improve test coverage:

- Add tests for uncovered code paths
- Write integration tests
- Report test failures

## Good First Issues

New to vrclog or open source? Look for issues labeled `good first issue`:

- [vrclog-go Good First Issues](https://github.com/vrclog/vrclog-go/labels/good%20first%20issue)
- [vrclog-adapters Good First Issues](https://github.com/vrclog/vrclog-adapters/labels/good%20first%20issue)
- [vrclog-companion Good First Issues](https://github.com/vrclog/vrclog-companion/labels/good%20first%20issue)

These issues are:
- Small and well-defined (typically 2-4 hours of work)
- Often focused on tests or documentation
- Great for learning the codebase

## Development Guide

### vrclog-go

#### Prerequisites

- **Go 1.25 or later**
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

### vrclog-adapters

#### Prerequisites

- **Go 1.25 or later**
- **Git**

#### Getting Started

1. Fork the repository
2. Clone your fork:
   ```bash
   git clone https://github.com/YOUR_USERNAME/vrclog-adapters.git
   cd vrclog-adapters
   ```
3. Create a branch for your changes:
   ```bash
   git checkout -b feature/your-adapter-name
   ```

#### Writing a New Adapter

Adapters are compile-time Go packages that decode log lines from a specific community project into `vrclog-go`'s canonical Event types. When contributing an adapter, keep these constraints in mind:

- **Stateless and record-local**: `Decode` must not perform I/O or depend on state from previous records.
- **Only canonical Event types**: Adapters may only emit the sealed Event types defined in `vrclog-go`. No custom event types.
- **Anchored rules**: Match patterns should be anchored to the project's own log prefix, not general-purpose URL searching.
- **Fixture-verified**: Every adapter must be verified against synthetic or fully redacted fixtures under `testdata/` that match the real source log format. Placeholder adapters without a fixture are not accepted.
- **No aggregate API**: There is no `All()` helper. Consumers explicitly import each adapter they want (`yamaplayer.New()`, `iwasync3.New()`, etc.), so adding a new adapter never silently changes an existing application's behavior.
- **Redact fixture content**: See [Fixture Privacy](#fixture-privacy) below before committing any log-derived test data.

#### Running Tests

```bash
go test ./...
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
go build -o vrclog-companion ./cmd/vrclog-companion
./vrclog-companion

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
- [ ] No secrets, raw logs, or unredacted credentials are committed
- [ ] Fixture data is redacted of personal information (if applicable – see [Fixture Privacy](#fixture-privacy))
- [ ] Breaking changes are documented (if applicable)
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

- Wording and phrasing translations may lag behind English – this is OK
- If you notice outdated translations, please open an issue or PR
- Ensure translations accurately convey the original meaning

### Exception: Factual Metadata Must Stay in Sync

Some content is factual rather than editorial, and letting it drift creates real confusion (for example, a Japanese reader being pointed at the wrong repository). The following must be updated in **both** English and Japanese in the same PR, or tracked with an explicit follow-up issue if that isn't possible:

- The list of organization repositories
- Supported Go/Node.js versions
- Public API examples (e.g., in `profile/README.md`)
- Security and privacy guidance (redaction requirements, scope, reporting process)

## Fixture Privacy

VRChat logs, and the adapter fixtures derived from them, can contain personal data: display names, user IDs, world/instance IDs, media URLs, local file paths, and more.

- **Prefer synthetic fixtures.** Construct log lines that match the real format without using data from an actual session.
- **If a real log excerpt is necessary**, it must be minimal and fully redacted before being committed:
  - Replace display names and user/world/instance IDs with placeholders
  - Replace media URLs with clearly fake placeholder URLs
  - Remove local file paths, tokens, and webhook URLs
  - Remove or adjust timestamps if they could identify a specific session

## Privacy Notice

When reporting issues or sharing logs:

> **Important**: VRChat logs contain usernames, world names, media URLs, and other information about yourself and others. **Never share raw logs publicly without redacting personal information.**

- Remove or redact other users' display names
- Remove or redact world instance IDs if they could identify specific sessions
- Remove or redact media URLs, local file paths, Discord webhook URLs, and any tokens or credentials
- When in doubt, ask a maintainer how to share information safely

## Code of Conduct

All contributors are expected to follow our [Code of Conduct](./CODE_OF_CONDUCT.md). Please read it before participating.

## Questions?

- Open an issue for project-related questions
- Email vrclog@googlegroups.com for private inquiries

Thank you for contributing to vrclog!
