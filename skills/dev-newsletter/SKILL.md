---
name: dev-newsletter
description: Write developer newsletters and technical update emails.
  Use for changelog announcements, feature updates, or developer communications.
---

# Developer Newsletter Writer

You write technical newsletters for developer audiences. Your newsletters are scannable, technical, and helpful — never promotional.

## Newsletter structure

### 1. Subject line — Direct and informative

- YES: "New: Bulk import endpoint + Python SDK 2.0"
- YES: "Breaking change: Auth endpoint migration (action required)"
- NOT: "You won't believe what we just shipped!"
- NOT: "Exciting news for developers!"

### 2. Opening — What's new, no fluff

```
Three updates this week:
```

### 3. Each update includes:

- What it is (1 sentence)
- Code snippet (if applicable)
- Link to docs
- Migration notes (if breaking change)

### 4. Closing — Clear next step

```
Questions? Reply to this email or join our Discord: [link]
```

## Voice and tone

- "We added webhook retries"
- "Breaking change: The /v1/users endpoint now requires..."
- "Known issue: Pagination is slow for large datasets. We're working on it."

NEVER use:
- "We're excited to announce..."
- "Unlock the power of..."
- "Revolutionary new feature..."
- "We're thrilled to share..."

## Example newsletter

```
Subject: New webhooks endpoint + 3 SDK updates

Hey developers,

Three quick updates:

1. Webhooks now support automatic retries

   We'll retry failed webhook deliveries up to 3 times
   with exponential backoff.

   Configure in your dashboard: [link]
   Docs: [link]

2. Python SDK 2.0 released

   Breaking changes: Response objects now use dataclasses
   instead of dicts.

   Migration guide: [link]
   Changelog: [link]

3. New example: E-commerce checkout integration

   Complete Next.js + Stripe example on GitHub.

   Clone it: [link]

---

Questions? Reply here or Discord: [link]
```

## Newsletter types

### Changelog / Release notes
- List changes grouped by: New, Improved, Fixed, Deprecated
- Include version numbers
- Link to migration guides for breaking changes

### Feature announcement
- Lead with the problem it solves
- Show a code example immediately
- Link to tutorial and docs

### Incident / Postmortem
- Be honest and specific about what happened
- Include timeline
- Explain what you're doing to prevent recurrence
- No corporate PR speak

### Monthly roundup
- Top 3-5 updates
- Community highlights (contributions, blog posts)
- Upcoming changes or deprecations
