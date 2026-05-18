# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| latest (`main`) | ✅ |
| older releases | ❌ |

We only provide security fixes on the `main` branch. Please make sure you are running the latest version before reporting.

---

## Reporting a Vulnerability

**Do not open a public GitHub issue for security vulnerabilities.**

Please report security issues privately via one of:

- **Email:** security@hermesmarketplace.xyz
- **GitHub Private Vulnerability Reporting:** [Report a vulnerability](../../security/advisories/new)

Include as much of the following as possible:

- Description of the vulnerability
- Steps to reproduce (proof of concept if available)
- Potential impact and affected components
- Your suggested fix, if any

We will acknowledge your report within **48 hours** and aim to provide an initial assessment within **5 business days**.

---

## Scope

The following are **in scope**:

- Authentication and authorisation bypasses (e.g. submitting skills owned by another user)
- API key or session token exposure
- SQL injection or Drizzle ORM query manipulation
- Cross-site scripting (XSS) in skill content rendered on detail pages
- Server-side request forgery (SSRF) via the GitHub URL fetch path
- Privilege escalation on agent API endpoints
- Any vulnerability allowing an attacker to modify or delete other users' skills

The following are **out of scope**:

- Denial of service via high request volume (rate limiting is a known gap)
- Issues in third-party dependencies with no active exploit (open a Dependabot PR instead)
- Social engineering attacks
- Security issues in Clerk's authentication infrastructure (report to Clerk directly)

---

## Disclosure Policy

We follow **coordinated disclosure**:

1. You report privately.
2. We investigate, confirm, and fix.
3. We release the fix and notify you.
4. We publish a security advisory crediting you (unless you prefer to remain anonymous).

We aim to resolve critical vulnerabilities within **7 days** and high-severity issues within **30 days**.

---

## Safe Harbour

We will not pursue legal action against researchers who:

- Report vulnerabilities in good faith following this policy
- Do not access, modify, or delete data beyond what is needed to demonstrate the issue
- Do not publicly disclose the vulnerability before we have released a fix

---

## Hall of Fame

We publicly thank researchers who responsibly disclose valid vulnerabilities (with their permission).

| Researcher | Finding | Date |
|------------|---------|------|
| *(be the first)* | | |
