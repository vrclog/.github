# Security Policy

- Japanese translation: [SECURITY.ja.md](./SECURITY.ja.md)

We take security seriously. This document outlines how to report security vulnerabilities and what to expect from the process.

## Important Notice

> **vrclog is an unofficial community project and is NOT affiliated with VRChat Inc.**
>
> vrclog tools read local VRChat log files on your machine. They do **not** have access to:
> - Your VRChat account credentials
> - VRChat's servers or APIs
> - Other users' accounts or data
>
> If you have concerns about your VRChat account security, please contact [VRChat Support](https://help.vrchat.com/) directly.

## Scope

This security policy covers vulnerabilities in:

- **vrclog-go**: Core Go library and CLI for reading, following, and parsing VRChat logs
- **vrclog-adapters**: Community-project adapters (YamaPlayer, iwaSync3, etc.)
- **vrclog-companion**: Local resident application with SQLite persistence, Web UI, HTTP API, and Discord notifications
- Official vrclog documentation and websites
- vrclog's GitHub organization infrastructure

Detailed, implementation-level security documentation (parser resource limits, authentication middleware behavior, storage retention, etc.) lives alongside each repository's own code. This document defines the shared reporting process and the security expectations that apply across all three repositories.

Direct implementation-specific security notes are available in [vrclog-go Privacy and Security](https://github.com/vrclog/vrclog-go/blob/main/README.md#privacy-and-security), [vrclog-adapters Privacy / redaction](https://github.com/vrclog/vrclog-adapters/blob/main/README.md#privacy--redaction), and [vrclog-companion Security & Privacy](https://github.com/vrclog/vrclog-companion/blob/main/README.md#security--privacy).

## Reporting a Vulnerability

### Do NOT

- Open a public GitHub issue for security vulnerabilities
- Disclose the vulnerability publicly before it has been addressed
- Share exploit code publicly

### Do

Report security vulnerabilities privately via email:

**Email**: vrclog@googlegroups.com

**Subject line**: `[SECURITY] Brief description of the issue`

### What to Include

Please provide as much information as possible:

1. **Description**: Clear description of the vulnerability
2. **Affected component**: Which repository (vrclog-go, vrclog-adapters, vrclog-companion, etc.)
3. **Affected versions**: Which versions are affected (if known)
4. **Reproduction steps**: How to reproduce the issue
5. **Impact assessment**: What could an attacker potentially do?
6. **Environment**: OS, Go version, Node.js version, tool version, etc.
7. **Suggested fix**: If you have ideas on how to fix it (optional)

## Response Process

### Timeline

| Phase | Timeframe |
|-------|-----------|
| Acknowledgment | Within 48 hours |
| Initial assessment | Within 14 days |
| Fix development | Varies by severity |
| Public disclosure | 90 days after report (may be extended for complex issues) |

### Disclosure Policy

We follow a coordinated disclosure policy:

- **Disclosure deadline**: 90 days from initial report
- **Extensions**: May be granted for complex vulnerabilities requiring more time to fix
- **Early disclosure**: May occur if a fix is released and verified before the deadline
- **Delayed disclosure**: May be requested for exceptionally severe vulnerabilities

### What to Expect

1. **Acknowledgment**: We will confirm receipt of your report within 48 hours
2. **Communication**: We will keep you informed of our progress
3. **Credit**: With your permission, we will credit you in the security advisory
4. **Coordinated disclosure**: We will work with you on timing of any public disclosure

### Severity Assessment

We assess vulnerabilities based on:

- **Impact**: What damage could result from exploitation?
- **Exploitability**: How easy is it to exploit?
- **Scope**: How many users are affected?
- **Attack vector**: Network, local, physical access required?

## Supported Versions

We provide security updates for:

| Version | Supported |
|---------|-----------|
| Latest release | Yes |
| Previous minor version | Best effort |
| Older versions | No |

We recommend always using the latest version.

## Security Best Practices for Users

### General

1. **Keep software updated**: Always use the latest version
2. **Be careful with logs**: VRChat logs contain personal information (usernames, world names, media URLs). Don't share them publicly without redaction
3. **Review configurations**: Regularly review any configuration files for unintended settings

### Discord Webhook URLs

vrclog-companion can send notifications through a Discord webhook. Treat the webhook URL as a credential:

- Never paste it into a public issue, PR, screenshot, or chat message
- Never commit it to a repository, including in `config.json` snippets
- Rotate the webhook immediately if it is ever exposed

### vrclog-adapters

1. **Use official adapters**: Only use adapters from the official [vrclog-adapters](https://github.com/vrclog/vrclog-adapters) repository or sources you trust
2. **Review before use**: Adapters interpret log content and may extract URLs from your local logs; review adapter source before adding a third-party adapter to your build

For fixture redaction and adapter-specific privacy guidance, see [vrclog-adapters Privacy / redaction](https://github.com/vrclog/vrclog-adapters/blob/main/README.md#privacy--redaction).

### vrclog-companion Network Exposure

1. **Network exposure**: Only enable LAN mode on trusted networks
2. **Basic Auth**: When LAN mode is enabled, ensure strong credentials are configured
3. **Firewall**: Do not expose vrclog-companion to the public internet
4. **Data directory**: Protect the data directory containing the SQLite database and configuration files

For implementation details behind these recommendations (default bind address, authentication middleware, token handling), see [vrclog-companion Security & Privacy](https://github.com/vrclog/vrclog-companion/blob/main/README.md#security--privacy).

## Acknowledgments

We appreciate the security research community's efforts in responsibly disclosing vulnerabilities. Contributors who report valid security issues will be acknowledged (with their permission) in our release notes.

## Contact

- **Security reports**: vrclog@googlegroups.com
- **General questions**: Open a GitHub issue
