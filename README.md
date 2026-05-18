# HermesMarketplace

<div align="center">

<img src="https://i.ibb.co/VY63vf4z/Bildschirmfoto-2026-05-18-um-03-26-40.png" alt="HermesMarketplace" width="100%" />

<br/>
<br/>

**The open skills marketplace for autonomous AI agents.**

Browse, install, and publish verified skills. Security-scanned. Community-driven. Built for the agentic era.

**[Visit Marketplace](https://hermes-agent-news.com/marketplace)** &nbsp;·&nbsp; **[Guidelines](https://hermes-agent-news.com/marketplace/guidelines)** &nbsp;·&nbsp; **[Submit a Skill](https://hermes-agent-news.com/skills/submit)**

</div>

---

## What is HermesMarketplace?

HermesMarketplace is a curated registry where developers publish skills — reusable capability modules that autonomous agents can install and execute. Every skill is reviewed by the Hermes autonomous agent for quality, safety, and consistency before it appears in the marketplace.

Skills follow a structured `SKILL.md` manifest standard and are versioned semantically. The marketplace tracks stars, upvotes, and AI quality scores so agents and developers can quickly surface the best tools for a given task.

---

## Features

| Feature | Description |
|---------|-------------|
| **AI Quality Scoring** | Every submission is evaluated across 5 dimensions: clarity, safety, completeness, determinism, and utility |
| **GitHub OAuth** | Sign in with GitHub — you can only submit repos you own, enforced server-side |
| **Author Profiles** | Skill cards display the author's GitHub avatar, username, follower count, and public repo count |
| **Ownership Enforcement** | Server verifies repo owner matches authenticated GitHub username — no impersonation possible |
| **Skill Detail Pages** | Install commands, language, stars, upvotes, quality label, and AI reviewer notes |
| **Agent API** | Hermes agent uploads and manages skills programmatically via bearer-token REST API |
| **Leaderboards** | Top skills ranked by stars, upvotes, and AI quality score |
| **Search and Filter** | Full-text search, category filters, sort modes (newest, top rated, most upvoted) |
| **Admin Panel** | Password-protected panel to approve, reject, or delete submissions |

---

## Installing Skills

```bash
# Install a skill directly
skill_manage install <github-username>/<repo-name>

# Browse the marketplace
open https://hermes-agent-news.com/marketplace

# Browse top-rated skills
open https://hermes-agent-news.com/marketplace?sort=score
```

---

## Submitting a Skill

1. Create a `SKILL.md` in your **public** GitHub repository following the [skill manifest spec](https://hermes-agent-news.com/marketplace/guidelines).
2. Sign in at [hermes-agent-news.com/skills/submit](https://hermes-agent-news.com/skills/submit) with your GitHub account.
3. Paste your repository URL — only repos you own are accepted.
4. The AI evaluator analyzes your skill and assigns a quality label within minutes.
5. Once approved, your skill appears in the marketplace with your GitHub profile.

---

## Skill Manifest (`SKILL.md`)

Every skill needs a `SKILL.md` at the repo root. Minimum required sections:

```markdown
# Skill Name

One sentence describing what this skill does.

## Inputs

- `param_name` (type, required/optional): description

## Outputs

- `result_name` (type): description

## Example

Input: { "param": "value" }
Output: { "result": "value" }

## Dependencies

- list any external APIs or packages called
```

See the full [submission guidelines](https://hermes-agent-news.com/marketplace/guidelines) for versioning, naming conventions, safety rules, and the review process.

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend (News + Marketplace) | React 19, Vite, Tailwind CSS, Wouter, Framer Motion |
| Skills App | React 19, Vite, Tailwind CSS, Clerk Auth |
| API Server | Express 5, Node.js 24, TypeScript 5.9 |
| Database | PostgreSQL + Drizzle ORM |
| Authentication | Clerk (GitHub OAuth) |
| Validation | Zod v4 |
| Monorepo | pnpm workspaces |
| CI | GitHub Actions (typecheck + dependency audit) |

---

## Development Setup

**Requirements:** Node.js 24+, pnpm 9+, PostgreSQL 15+

```bash
# Clone and install
git clone https://github.com/your-org/hermes-marketplace
cd hermes-marketplace
pnpm install

# Set up environment
cp .env.example .env
# Edit .env with your DATABASE_URL, Clerk keys, and AGENT_API_KEY

# Push database schema
pnpm --filter @workspace/db run push

# Start all services
pnpm --filter @workspace/api-server run dev    # API  → :5000
pnpm --filter @workspace/hermes-news run dev    # UI   → :PORT
pnpm --filter @workspace/hermes-skills run dev  # Auth → :PORT

# Full typecheck
pnpm run typecheck
```

---

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for development setup, branch conventions, and PR guidelines.

We welcome:
- New skill submissions via the marketplace
- Bug reports and feature requests via GitHub Issues
- Pull requests following the branch and commit conventions

---

## Security

Found a vulnerability? Email **hermesagentsol@proton.me** and report it **privately** — do not open a public issue.

---

## License

MIT — see [LICENSE](./LICENSE).

---

## Links

- [Marketplace](https://hermes-agent-news.com/marketplace)
- [Submit a Skill](https://hermes-agent-news.com/skills/submit)
- [Guidelines](https://hermes-agent-news.com/marketplace/guidelines)
- [X / Twitter — @HermesAgentSol](https://x.com/HermesAgentSol)
