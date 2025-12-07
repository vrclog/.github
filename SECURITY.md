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

- vrclog libraries and tools (e.g., `vrclog-go`)
- Official vrclog documentation and websites
- vrclog's GitHub organization infrastructure

## Potential Security Concerns

Given the nature of vrclog (parsing local log files), potential security issues may include:

### Data Exposure Risks

- **Log path disclosure**: Exposing file system paths that could reveal sensitive directory structures
- **Username/World name leakage**: Inadvertent exposure of usernames, world names, or instance IDs from logs
- **Session information**: Leaking information that could identify specific play sessions

### Application Security

- **Path traversal**: Vulnerabilities allowing access to files outside intended directories
- **Command injection**: In CLI tools, improper handling of user input
- **Network exposure**: If running in server mode, unintended network accessibility or data exposure

### Privacy Concerns

- **Inadequate data sanitization**: Failing to properly redact sensitive information
- **Unintended data collection**: Collecting or transmitting data without user consent

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
2. **Affected versions**: Which versions are affected (if known)
3. **Reproduction steps**: How to reproduce the issue
4. **Impact assessment**: What could an attacker potentially do?
5. **Environment**: OS, Go version, tool version, etc.
6. **Suggested fix**: If you have ideas on how to fix it (optional)

## Response Process

### Timeline

| Phase | Timeframe |
|-------|-----------|
| Acknowledgment | Within 7 days |
| Initial assessment | Within 14 days |
| Fix development | Varies by severity |
| Public disclosure | After fix is released |

### What to Expect

1. **Acknowledgment**: We will confirm receipt of your report within 7 days
2. **Communication**: We will keep you informed of our progress
3. **Credit**: With your permission, we will credit you in the security advisory
4. **Coordinated disclosure**: We will work with you on timing of any public disclosure

### Severity Assessment

We assess vulnerabilities based on:

- **Impact**: What damage could result from exploitation?
- **Exploitability**: How easy is it to exploit?
- **Scope**: How many users are affected?

## Supported Versions

We provide security updates for:

| Version | Supported |
|---------|-----------|
| Latest release | Yes |
| Previous minor version | Best effort |
| Older versions | No |

We recommend always using the latest version.

## Security Best Practices for Users

When using vrclog tools:

1. **Keep software updated**: Always use the latest version
2. **Be careful with logs**: VRChat logs contain personal information (usernames, world names). Don't share them publicly without redaction
3. **Network exposure**: If running server modes, ensure proper firewall configuration
4. **Review configurations**: Regularly review any configuration files for unintended settings

## Acknowledgments

We appreciate the security research community's efforts in responsibly disclosing vulnerabilities. Contributors who report valid security issues will be acknowledged (with their permission) in our release notes.

## Contact

- **Security reports**: vrclog@googlegroups.com
- **General questions**: Open a GitHub issue
