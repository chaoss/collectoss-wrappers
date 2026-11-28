# Security Policy

## Supported Versions

None of the wrappers has a tagged release yet. Until the first one, security fixes go to the `main` branch.

## Reporting a Vulnerability

**IMPORTANT: Do not report security vulnerabilities using public GitHub Issues or public discussions.**

### Private Disclosure Process

If you discover a security vulnerability in one of the wrappers, please report it privately by opening a [New Private Vulnerability Report](https://github.com/chaoss/collectoss-wrappers/security/advisories/new). Please fill out the [advisory template](.github/SECURITY_ADVISORY_TEMPLATE.md) so we have the details (Impact, Reproduction Steps, and Affected Versions) needed to investigate.

### Scope

This policy covers the code in this repository: how a wrapper downloads, verifies, caches and runs its binary, its Python API, and the CI workflows.

A vulnerability in a wrapped binary itself, for example in `disclosure`, belongs to that project. Please contact its maintainers privately instead of opening a public issue: for `disclosure`, reach out on the CHAOSS Slack in `#data-ai-disclosure-detection`. If you are not sure where it belongs, report it here and we will route it.

### Responsible Disclosure Guidelines

We do our best to follow responsible disclosure practices:

- **Credit**: We will acknowledge your discovery in security release notes (unless you prefer anonymity)
- **Coordination**: We will work with you to coordinate the disclosure and release timeline based on our capacity to resolve the issue
- **Communication**: We aim to remain communicative and keep your ticket updated with the status so you know what to expect
- **No Public Issues**: Please avoid creating public GitHub issues, pull requests, branches, or forks for developing fixes to security vulnerabilities unless told otherwise. All of these can leak the existence of the vulnerability before it is fully fixed.

Thank you for helping keep the CollectOSS wrappers secure!

## Security Response Committee

The current Security Response Committee consists of the [CollectOSS Maintainers](https://github.com/chaoss/CollectOSS/blob/main/MAINTAINERS.md).
