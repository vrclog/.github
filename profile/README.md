# vrclog

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

**Open-source tools for turning VRChat local logs into structured, useful data.**

vrclog is a set of local-first tools and Go libraries for reading VRChat PC log files, extracting structured observations, and building applications on top of them.

The ecosystem can track things such as:

* player joins and leaves
* world transitions
* media playback attempts and errors
* original media URLs recorded by VRChat
* observations emitted by community world assets such as YamaPlayer and iwaSync3

> **Note**: vrclog is an unofficial community project and is **not affiliated with VRChat Inc.** All tools operate locally on your machine and do not upload data to any cloud services by default.

## Architecture

The project is split into three cooperating repositories:

```text
VRChat output_log_*.txt
        │
        ▼
┌──────────────────────────────────────┐
│ vrclog-go                             │
│                                        │
│ Read / Follow                         │
│      │                                │
│      ▼                                │
│    Record                             │
│      │                                │
│      ▼                                │
│    Engine                             │
│      │                                │
│      ▼                                │
│ canonical Event                       │
│      │                                │
│      ▼                                │
│ Observation + provenance              │
└──────────────────────────────────────┘
        ▲
        │ community Adapters
┌──────────────────────────────────────┐
│ vrclog-adapters                       │
│                                        │
│ YamaPlayer                            │
│ iwaSync3                              │
│ ...                                    │
└──────────────────────────────────────┘

        Observation stream
                │
                ▼
┌──────────────────────────────────────┐
│ vrclog-companion                      │
│                                        │
│ SQLite persistence                    │
│ World / Presence / Media projectors   │
│ HTTP API + SSE                        │
│ Web UI                                │
│ optional notifications                │
└──────────────────────────────────────┘
```

The important boundary is the **Observation** model.

Log formats and community-specific quirks are interpreted at the ingestion layer, while applications consume a canonical stream with provenance describing where each observation came from.

## Repositories

| Repository | Role | Use it when... |
|------------|------|-----------------|
| [vrclog-go](https://github.com/vrclog/vrclog-go) | Core Go library and CLI | You want to read/follow VRChat logs or build your own application |
| [vrclog-adapters](https://github.com/vrclog/vrclog-adapters) | Community-project adapters | You need to interpret logs produced by assets such as YamaPlayer or iwaSync3 |
| [vrclog-companion](https://github.com/vrclog/vrclog-companion) | End-user local application | You want persistence, projected state, media recovery, a Web UI, API, or notifications |

### `vrclog-go`

The foundation of the ecosystem.

It provides:

* VRChat log discovery and reading
* live log following
* physical log records with stable provenance
* the Adapter interface
* the processing Engine
* canonical Event types
* Observation generation
* a built-in adapter for VRChat client logs
* JSONL CLI output

```go
engine, err := vrclog.NewEngine(
    vrclog.NewVRChatAdapter(),
)
```

Repository:

https://github.com/vrclog/vrclog-go

### `vrclog-adapters`

Compile-time adapters for log formats emitted by community VRChat projects.

Currently verified:

| Project    | Adapter                | Status                             |
|------------|-------------------------|-------------------------------------|
| YamaPlayer | `community.yamaplayer` | Verified against synthetic fixtures matching the real log format |
| iwaSync3   | `community.iwasync3`   | Verified against synthetic fixtures matching the real log format |

These adapters emit the same canonical event types defined by `vrclog-go`. There is no aggregate "all adapters" API — each adapter is imported explicitly:

```go
engine, err := vrclog.NewEngine(
    vrclog.NewVRChatAdapter(),
    yamaplayer.New(),
    iwasync3.New(),
)
```

Repository:

https://github.com/vrclog/vrclog-adapters

### `vrclog-companion`

A local resident application built on top of `vrclog-go` and `vrclog-adapters`.

It continuously consumes VRChat logs and turns the Observation stream into usable application state.

Features include:

* continuous VRChat log ingestion
* SQLite persistence
* World state projection
* Presence state projection
* Media state projection
* HTTP JSON API
* Server-Sent Events
* Web UI
* optional Discord notifications

Repository:

https://github.com/vrclog/vrclog-companion

## Media URL recovery

One of the main use cases for vrclog is recovering media URLs from VRChat logs.

A video player inside a world may fail for one user even though playback works for everyone else. In many cases, VRChat still writes information about the original media URL to its local log.

vrclog can interpret and correlate those records so applications such as `vrclog-companion` can expose the original URL without guessing the URL or querying an external metadata service.

Support currently includes observations from:

* VRChat's built-in video logging
* YamaPlayer
* iwaSync3

> **Privacy note**: Recovered media URLs may reveal private session context, watched content, or service-specific access tokens embedded in logs. Do not publish recovered URLs, screenshots, or raw logs unless you have removed personal data and confirmed the URL is safe to share. Treat recovered URLs as sensitive by default.

## Local-first

vrclog is designed around local processing.

VRChat log files may contain sensitive information such as:

* player display names
* world information
* media URLs
* private or signed URLs

For that reason:

* log processing happens locally
* `vrclog-companion` stores its database locally in SQLite
* there is no mandatory cloud backend
* there is no telemetry requirement
* network integrations such as Discord notifications are optional

The core libraries do not require an external service to interpret logs.

## Building on vrclog

If you are writing a Go application that consumes VRChat logs, start with:

**[`vrclog-go`](https://github.com/vrclog/vrclog-go)**

If your application also needs community-player support, add:

**[`vrclog-adapters`](https://github.com/vrclog/vrclog-adapters)**

If you simply want a ready-to-run application rather than a library, use:

**[`vrclog-companion`](https://github.com/vrclog/vrclog-companion)**

## Project principles

The repositories are intentionally separated by responsibility:

**Core semantics belong in `vrclog-go`.**
File I/O, records, cursors, canonical events, observations, provenance, and engine behavior should not depend on individual community projects.

**Community-specific parsing belongs in `vrclog-adapters`.**
YamaPlayer, iwaSync3, and similar projects should not become dependencies of the core library.

**Application behavior belongs in `vrclog-companion`.**
Persistence, state projection, APIs, user interfaces, and notifications are application concerns rather than parsing concerns.

This keeps the core library reusable while allowing support for the VRChat ecosystem to grow independently.

## Contributing

Issues, bug reports, adapter fixtures, compatibility reports, documentation improvements, and pull requests are welcome.

Before contributing, see the organization-wide contribution guidelines:

[CONTRIBUTING.md](https://github.com/vrclog/.github/blob/main/CONTRIBUTING.md)

Security-sensitive reports should follow:

[SECURITY.md](https://github.com/vrclog/.github/blob/main/SECURITY.md)

## License

The vrclog projects are released under the MIT License.

---

<sub>vrclog is an unofficial community project and is not affiliated with or endorsed by VRChat Inc. VRChat is a trademark of VRChat Inc.</sub>
