# Contributing to AI Peer

Thank you for your interest in contributing! This document provides guidelines and instructions.

## Code of Conduct

Please read and follow our [Code of Conduct](CODE_OF_CONDUCT.md).

## How to Contribute

### Reporting Bugs

1. Check if the bug has already been reported in [Issues](https://github.com/nicepkg/ai-peer/issues)
2. If not, create a new issue with:
   - Steps to reproduce
   - Expected vs actual behavior
   - Python version and OS
   - Relevant logs from `~/.ai-peers/daemon.log`

### Suggesting Features

1. Check if the feature has already been suggested in [Issues](https://github.com/nicepkg/ai-peer/issues)
2. If not, create a new issue explaining:
   - The use case
   - Why existing features don't cover it
   - Proposed solution (optional)

### Pull Requests

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes
4. Add tests for new functionality
5. Run the test suite:
   ```bash
   PYTHONPATH=skills/ai-peer/scripts \
     uv run --with pytest --with cryptography \
     pytest skills/ai-peer/tests/ -v
   ```
6. Commit your changes: `git commit -m "feat: add your feature"`
7. Push to your fork: `git push origin feature/your-feature-name`
8. Open a Pull Request

### Commit Convention

We follow [Conventional Commits](https://www.conventionalcommits.org/):

- `feat:` — New feature
- `fix:` — Bug fix
- `docs:` — Documentation only
- `test:` — Adding or updating tests
- `refactor:` — Code change that neither fixes a bug nor adds a feature
- `chore:` — Maintenance tasks

## Development Setup

```bash
git clone https://github.com/nicepkg/ai-peer.git
cd ai-peer

# Verify Python version
python3 --version  # Must be 3.10+

# Run tests
PYTHONPATH=skills/ai-peer/scripts \
  uv run --with pytest --with cryptography \
  pytest skills/ai-peer/tests/ -v

# Start daemon for manual testing
PYTHONPATH=skills/ai-peer/scripts python3 -m ai_peer daemon start
PYTHONPATH=skills/ai-peer/scripts python3 -m ai_peer daemon status
```

## Architecture

See [How It Works](README.md#-how-it-works) in the README and the [PRD](skills/ai-peer/references/PRD.md) for detailed architecture documentation.

Key principles:
- **Zero pip dependencies** for core functionality
- **Python stdlib only** — `cryptography` is optional for E2E encryption
- **Cross-platform** — macOS, Linux, Windows
- **Tests required** for new features

## Project Structure

```
ai-peer/
├── skills/ai-peer/
│   ├── SKILL.md              # Skill definition (read by AI agents)
│   ├── scripts/
│   │   ├── ai_peer/          # Python package (CLI + daemon)
│   │   └── relay/            # Cloudflare Worker (relay server)
│   ├── tests/                # Test suite (69 tests)
│   └── references/           # PRD, setup docs
├── README.md                 # English documentation
├── README_cn.md              # Chinese documentation
└── LICENSE                   # MIT
```

## Questions?

Open an issue or start a discussion on [GitHub](https://github.com/nicepkg/ai-peer/issues).
