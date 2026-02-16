# devrelskills

AI-powered skills for developer relations content. Adapted from [marketingskills](https://github.com/coreyhaines31/marketingskills) for developer audiences.

## What is this?

A collection of Claude Code skills that generate **developer-appropriate content** — tutorials with working code, API documentation, technical newsletters, and social posts that developers actually want to read.

Generic AI produces marketing fluff. These skills produce technical content.

**Without skills:**
> "Unlock the power of our revolutionary API! Streamline your workflow and leverage cutting-edge technology!"

**With devrelskills:**
> New endpoint: `POST /v2/bulk-import`. Import up to 10,000 records per request. Average processing time: 2.3 seconds.
> ```js
> const response = await fetch('https://api.example.com/v2/bulk-import', {
>   method: 'POST',
>   headers: { 'Authorization': `Bearer ${API_KEY}` },
>   body: JSON.stringify({ records: data })
> });
> ```

## Skills included

| Skill | Description | Use when... |
|---|---|---|
| `technical-tutorial` | Code-first tutorials with working examples | Writing integration guides, how-tos, getting started docs |
| `api-docs-audit` | Documentation completeness checker | Reviewing API docs for gaps and improvements |
| `code-examples` | Multi-language code samples | Generating SDK examples in curl, JS, Python, Go |
| `dev-newsletter` | Technical update emails | Writing changelogs, feature announcements, dev updates |
| `tech-social` | Developer social content | Creating Twitter threads and LinkedIn posts for launches |

## Quick start

### 1. Install Claude Code

```bash
# See https://docs.anthropic.com/en/docs/claude-code
```

### 2. Install devrelskills

Copy the skills into your Claude Code skills directory:

```bash
cp -r skills/* ~/.claude/skills/
```

Or clone and symlink:

```bash
git clone https://github.com/YOUR_USERNAME/devrelskills.git
ln -s $(pwd)/devrelskills/skills/* ~/.claude/skills/
```

### 3. Use a skill

Open Claude Code and invoke any skill:

```
/technical-tutorial
Write a tutorial for adding OAuth 2.0 to a Next.js app

/api-docs-audit
Audit our POST /users endpoint documentation

/code-examples
Generate examples for creating a user via POST /users

/dev-newsletter
Write a newsletter announcing webhook retries and Python SDK 2.0

/tech-social
Create a Twitter thread announcing automatic webhook retries
```

## Real workflow: API feature launch

Use all 5 skills together for a complete launch:

1. `/api-docs-audit` — Check existing docs for gaps
2. `/code-examples` — Generate examples in 3 languages
3. `/technical-tutorial` — Create complete integration guide
4. `/dev-newsletter` — Write announcement email
5. `/tech-social` — Create Twitter thread

**Time without skills:** 12-18 hours
**Time with skills:** 3-4 hours
**Savings:** ~70%

## Project structure

```
devrelskills/
├── skills/
│   ├── technical-tutorial/SKILL.md   # Tutorial writer
│   ├── api-docs-audit/SKILL.md       # Docs auditor
│   ├── code-examples/SKILL.md        # Code sample generator
│   ├── dev-newsletter/SKILL.md       # Newsletter writer
│   └── tech-social/SKILL.md          # Social content creator
├── tutorials/
│   ├── 01-why-devrel-needs-different-automation.md
│   ├── 02-building-technical-tutorial-skill.md
│   └── 03-five-essential-devrel-skills.md
├── examples/
│   ├── api-launch-workflow.md
│   ├── skill-audit-checklist.md
│   └── outputs/
│       ├── technical-tutorial-example.md
│       ├── api-docs-audit-example.md
│       ├── code-examples-example.md
│       ├── dev-newsletter-example.md
│       └── tech-social-example.md
├── docs/
│   └── adapting-marketing-skills.md
├── CONTRIBUTING.md
└── LICENSE
```

## Background

Most marketing automation tools are optimized for conversion — moving someone from awareness to purchase. That works for B2C, but developers operate differently:

- Code comes first, explanation second
- Show, don't sell
- Respect technical knowledge
- Completeness over cleverness
- Honesty about limitations

These skills enforce those principles. Every tutorial starts with working code. Every example is complete and copy-pastable. No marketing buzzwords allowed.

## Credits

- Built on [marketingskills](https://github.com/coreyhaines31/marketingskills) by Corey Haines
- Inspired by Anthropic's growth team learnings on Claude Code for marketing automation

## License

MIT
