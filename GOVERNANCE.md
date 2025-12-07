# Governance

- Japanese translation: [GOVERNANCE.ja.md](./GOVERNANCE.ja.md)

This document describes how the vrclog project is governed and how decisions are made.

## Overview

vrclog is a community-driven open source project. We aim to be transparent about how the project is run and how contributors can become more involved.

## Roles

### Contributors

Anyone who contributes to the project in any way:

- Opening issues or participating in discussions
- Submitting pull requests
- Improving documentation
- Helping other users
- Providing translations

Contributors are the lifeblood of the project. We appreciate all contributions, no matter how small.

### Maintainers

Maintainers are contributors who have demonstrated sustained commitment to the project. They have additional responsibilities:

- Reviewing and merging pull requests
- Triaging issues
- Making releases
- Guiding the project's direction
- Enforcing the Code of Conduct

Maintainers are listed in the [CODEOWNERS](./CODEOWNERS) file.

## Decision Making

### Day-to-Day Decisions

For routine matters (bug fixes, small improvements, documentation updates):

- Any maintainer can review and merge PRs
- Use good judgment – when in doubt, ask for a second opinion

### Significant Decisions

For changes that affect the project more broadly, we seek consensus through discussion:

**Examples of significant decisions:**

- API changes that break backward compatibility
- Changes to the event schema or data structures
- Adding new major features
- Changes to project governance
- Licensing changes

**Process:**

1. Open an issue describing the proposed change
2. Allow time for community discussion (typically 1-2 weeks for major changes)
3. Maintainers will summarize the discussion and make a decision
4. Document the decision in the issue before proceeding

### Conflict Resolution

If maintainers disagree on a decision:

1. Discuss the issue openly in the relevant GitHub issue
2. Seek input from the community
3. If consensus cannot be reached, the maintainer with the most relevant expertise makes the final call
4. Decisions can be revisited if new information emerges

## Release Policy

We follow [Semantic Versioning (SemVer)](https://semver.org/):

- **MAJOR** version: incompatible API changes
- **MINOR** version: new functionality in a backward-compatible manner
- **PATCH** version: backward-compatible bug fixes

### Version Guidelines

- **v0.x.y**: Development phase. APIs may change between minor versions.
- **v1.0.0+**: Stable API. Breaking changes require a new major version.

### Release Process

1. Maintainer prepares release notes
2. Version is tagged in git
3. Release is published to GitHub Releases
4. Announcement posted (if applicable)

## Becoming a Maintainer

We welcome new maintainers! There is no formal application process, but maintainers are typically invited based on:

- **Sustained contributions**: Regular, quality contributions over time (code, reviews, documentation, translations)
- **Community involvement**: Helping others, participating in discussions, and being a positive presence
- **Alignment with project values**: Following the Code of Conduct and supporting the project's goals
- **Technical judgment**: Demonstrating good judgment in code reviews and technical decisions

If you're interested in becoming a maintainer, the best approach is to:

1. Start contributing regularly
2. Help with issue triage and code reviews
3. Be active in discussions
4. Express your interest to existing maintainers

Current maintainers will discuss and reach consensus before extending an invitation.

## Changes to Governance

This governance document may be updated as the project evolves. Changes to governance follow the same process as other significant decisions.

## Contact

- **General questions**: Open a GitHub issue
- **Private matters**: Email vrclog@googlegroups.com
- **Security issues**: See [SECURITY.md](./SECURITY.md)
