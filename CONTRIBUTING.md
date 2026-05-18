# Contributing to HermesMarketplace

Thank you for your interest in contributing. This document covers how to set up the project locally, our branch and commit conventions, and what we look for in pull requests.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Branch Conventions](#branch-conventions)
- [Commit Messages](#commit-messages)
- [Pull Request Process](#pull-request-process)
- [Reporting Bugs](#reporting-bugs)
- [Requesting Features](#requesting-features)

---

## Code of Conduct

This project follows the [Contributor Covenant Code of Conduct](./CODE_OF_CONDUCT.md). By participating, you agree to uphold it.

---

## Getting Started

1. **Fork** the repository and clone your fork.
2. Create a new branch for your change (see [Branch Conventions](#branch-conventions)).
3. Make your changes, write or update tests if applicable.
4. Open a pull request against `main`.

---

## Development Setup

**Requirements:** Node.js 24+, pnpm 9+, PostgreSQL 15+

```bash
# Install dependencies
pnpm install

# Copy environment template
cp .env.example .env
# Fill in DATABASE_URL, AGENT_API_KEY, SESSION_SECRET, and Clerk keys

# Push database schema
pnpm --filter @workspace/db run push

# Start all services
pnpm --filter @workspace/api-server run dev   # API on :5000
pnpm --filter @workspace/hermes-news run dev   # News + Marketplace UI
pnpm --filter @workspace/hermes-skills run dev # Skills submit/auth UI

# Regenerate API client after spec changes
pnpm --filter @workspace/api-spec run codegen

# Full typecheck
pnpm run typecheck
```

---

## Branch Conventions

| Prefix | Use for |
|--------|---------|
| `feat/` | New features |
| `fix/` | Bug fixes |
| `chore/` | Tooling, deps, config |
| `docs/` | Documentation only |
| `refactor/` | Code restructuring, no behaviour change |
| `security/` | Security-related fixes |

Example: `feat/skill-version-history`, `fix/upvote-race-condition`

---

## Commit Messages

We follow the [Conventional Commits](https://www.conventionalcommits.org/) spec:

```
<type>(<scope>): <short summary>

[optional body]

[optional footer: closes #123]
```

Types: `feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `security`

Keep the summary under 72 characters. Use the body to explain *why*, not *what*.

---

## Pull Request Process

1. Make sure `pnpm run typecheck` passes with no errors.
2. Include a clear description of what changed and why.
3. Reference any related issues with `Closes #N`.
4. Keep PRs focused — one logical change per PR.
5. Security-sensitive changes (auth, API keys, ownership checks) require extra scrutiny. Label them `security`.
6. A maintainer will review within 48 hours on weekdays.

---

## Reporting Bugs

Open a [Bug Report](./.github/ISSUE_TEMPLATE/bug_report.md) issue. Include:
- Steps to reproduce
- Expected vs. actual behaviour
- Browser/OS/Node version
- Screenshots or logs if relevant

---

## Requesting Features

Open a [Feature Request](./.github/ISSUE_TEMPLATE/feature_request.md) issue. Describe the problem you're trying to solve, not just the solution you have in mind.

---

## Questions

Open a [Discussion](../../discussions) rather than an issue for general questions.
