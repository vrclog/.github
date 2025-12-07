# Support

- Japanese translation: [SUPPORT.ja.md](./SUPPORT.ja.md)

This document explains how to get help with vrclog projects and what kind of support we can provide.

## Important Notice

> **vrclog is an unofficial community project and is NOT affiliated with VRChat Inc.**
>
> We cannot provide support for:
> - VRChat application bugs or crashes
> - VRChat account issues (bans, suspensions, login problems)
> - VRChat's official features or services
>
> For VRChat-related issues, please contact [VRChat Support](https://help.vrchat.com/).

## Support Channels

### GitHub Issues

**Primary support channel for vrclog tools**

- [vrclog-go Issues](https://github.com/vrclog/vrclog-go/issues)

Use GitHub Issues for:
- Bug reports
- Feature requests
- Questions about using vrclog tools
- Documentation issues

### GitHub Discussions

*Coming soon* - We may enable GitHub Discussions for more open-ended conversations.

### Email

For private inquiries: vrclog@googlegroups.com

Use email for:
- Security vulnerabilities (see [SECURITY.md](./SECURITY.md))
- Private matters that shouldn't be discussed publicly
- Governance or administrative questions

## What We Support

### In Scope

We provide support for:

| Topic | Description |
|-------|-------------|
| **vrclog tools** | Installation, configuration, and usage of vrclog libraries and CLI |
| **Bug reports** | Issues with vrclog software behavior |
| **Feature requests** | Suggestions for new functionality |
| **Documentation** | Clarifications and improvements to docs |
| **Integration help** | Using vrclog libraries in your own projects |

### Out of Scope

We cannot help with:

| Topic | Where to Get Help |
|-------|-------------------|
| VRChat application issues | [VRChat Support](https://help.vrchat.com/) |
| VRChat account problems | [VRChat Support](https://help.vrchat.com/) |
| Network/ISP issues | Your ISP or network administrator |
| General Go programming | [Go Forum](https://forum.golanggo.dev/), Stack Overflow |
| Windows system issues | Microsoft Support |
| Hardware problems | Your hardware vendor |

## Support Expectations

### Response Times

vrclog is maintained by volunteers. Please understand that:

- **We cannot guarantee response times**
- Responses may take days or weeks depending on maintainer availability
- Complex issues may take longer to investigate

### Priority

We prioritize issues in the following order:

1. **Security vulnerabilities** - Handled privately and urgently
2. **Critical bugs** - Issues that prevent basic functionality
3. **Regular bugs** - Issues that affect normal usage
4. **Feature requests** - New functionality suggestions
5. **Questions** - General usage questions

## Before Asking for Help

To help us help you faster:

### 1. Search Existing Issues

Your question may already be answered. Search:
- [Open issues](https://github.com/vrclog/vrclog-go/issues)
- [Closed issues](https://github.com/vrclog/vrclog-go/issues?q=is%3Aissue+is%3Aclosed)

### 2. Gather Information

When reporting issues, please include:

- **Tool and version**: e.g., `vrclog-go v0.1.0`
- **Operating system**: e.g., Windows 11 23H2
- **Go version** (if building from source): e.g., `go1.22.0`
- **Steps to reproduce**: What did you do?
- **Expected behavior**: What did you expect to happen?
- **Actual behavior**: What actually happened?
- **Logs or error messages**: Include relevant output

### 3. Protect Privacy

VRChat logs contain personal information. Before sharing:

- **Remove usernames** of other players
- **Remove world instance IDs** if they could identify specific sessions
- **Remove any other personal information**

See our [Contributing Guide](./CONTRIBUTING.md) for more details on privacy.

## VRChat Log Location

For reference, VRChat stores logs in:

```
%LOCALAPPDATA%Low\VRChat\VRChat\
```

Typically: `C:\Users\<YourUsername>\AppData\LocalLow\VRChat\VRChat\`

Log files are named like: `output_log_YYYY-MM-DD_HH-MM-SS.txt`

## Community Guidelines

When seeking support, please:

- Be respectful and patient
- Provide clear, detailed information
- Follow up if you find a solution (it helps others!)
- Follow our [Code of Conduct](./CODE_OF_CONDUCT.md)

## Contributing Back

Found the answer to your question? Consider:

- Improving documentation
- Answering similar questions from others
- Contributing code fixes

See our [Contributing Guide](./CONTRIBUTING.md) for how to get involved.
