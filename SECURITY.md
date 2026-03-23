# Security Policy

## Reporting a Vulnerability

We take the security of AI Peer seriously. If you discover a security vulnerability, please report it responsibly.

### How to Report

1. **GitHub Issues**: Open an issue at [github.com/nicepkg/ai-peer/issues](https://github.com/nicepkg/ai-peer/issues) with the **"security"** label
2. **Private disclosure**: Use [GitHub Security Advisories](https://github.com/nicepkg/ai-peer/security/advisories/new) for sensitive vulnerabilities

### What to Include

- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

### Response Timeline

- **Acknowledgment**: Within 48 hours
- **Initial assessment**: Within 1 week
- **Fix release**: Depends on severity (critical: ASAP, high: 1-2 weeks)

## Security Architecture

### Local Daemon
- Listens on `127.0.0.1:7899` by default (localhost only)
- No authentication on local API (any local process can access)
- Use `--password` for E2E encryption on sensitive conversations

### Public Relay
- Room token required for access (32-byte hex)
- Per-peer HMAC-SHA256 signature authentication
- Relay overwrites peer identity from stored records (anti-impersonation)
- E2E encryption: relay stores only ciphertext (zero-knowledge)

### Known Limitations
- Local daemon has no auth (by design — localhost trust model)
- Room passwords stored in plaintext in SQLite (OS file permissions protect)
- LAN mode (`--lan`) exposes daemon to local network without auth

## Supported Versions

| Version | Supported |
|---------|-----------|
| 1.0.x   | ✅        |
