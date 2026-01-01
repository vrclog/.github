# vrclog

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

**Open-source tools and libraries for VRChat logs, sessions, and insights.**

---

## About

vrclog is a community-driven organization developing open-source tools to help VRChat users work with their local log files. Our tools monitor and parse VRChat PC log files, enabling structured access to events like:

- Player joins and leaves
- World transitions
- Session tracking
- Discord notifications
- Web-based dashboards

> **Note**: vrclog is an unofficial community project and is **not affiliated with VRChat Inc.** All tools operate locally on your machine and do not upload data to any cloud services by default.

## Repositories

| Repository | Description | Status | Language |
|------------|-------------|--------|----------|
| [vrclog-go](https://github.com/vrclog/vrclog-go) | Core library and CLI for VRChat log parsing | Active | Go |
| [vrclog-companion](https://github.com/vrclog/vrclog-companion) | Log watcher with SQLite persistence, Web UI & Discord notifications | Active | Go, TypeScript |

## Features

### vrclog-go
- Parse VRChat log files into structured events
- Real-time log monitoring (like `tail -f`)
- JSON Lines output for easy processing with `jq`
- Human-readable pretty output format

### vrclog-companion
- VRChat log monitoring with event persistence (SQLite)
- Web UI for browsing session history
- Discord webhook notifications with batching
- Real-time updates via SSE (Server-Sent Events)
- HTTP API for integration with other tools

## Future Plans

We aim to continue expanding the vrclog ecosystem with:

- Enhanced analytics and statistics
- Additional notification integrations
- Cross-platform support improvements
- Community-requested features

## Community

- **Issues & Discussions**: [vrclog-go](https://github.com/vrclog/vrclog-go/issues) | [vrclog-companion](https://github.com/vrclog/vrclog-companion/issues)
- **Contact**: vrclog@googlegroups.com

## Language Policy

- **English** is the primary language for documentation and code
- **Japanese (日本語)** translations are provided for major documents
- Contributions in both languages are welcome!

## Contributing

We welcome contributions from everyone! Please see our [Contributing Guide](https://github.com/vrclog/.github/blob/main/CONTRIBUTING.md) to get started.

---

<sub>vrclog is a community project. VRChat is a trademark of VRChat Inc.</sub>
