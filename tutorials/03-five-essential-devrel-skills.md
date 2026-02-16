# Five Essential Skills for a Developer Content Strategy

> Part 3 of the DevRel Skills series

In Part 2, we built the `technical-tutorial` skill. Now we'll create 4 more skills that work together to cover all DevRel content needs.

## The 5 skills

| Skill | Build time | Purpose |
|---|---|---|
| `technical-tutorial` | Built in Part 2 | Code-first tutorials |
| `api-docs-audit` | 10 min | Documentation review |
| `code-examples` | 10 min | Multi-language samples |
| `dev-newsletter` | 10 min | Technical update emails |
| `tech-social` | 10 min | Developer social content |

## Skill 1: API Documentation Audit

Reviews your API docs for completeness and gaps.

```bash
mkdir -p ~/.claude/skills/api-docs-audit
```

**What it checks per endpoint:**
- Completeness (parameters, responses, errors, rate limits, auth)
- Code examples (2+ languages, auth shown, copy-pastable)
- Response examples (success + all error codes)
- Missing items (pagination, webhooks, versioning, migration)

**Output format:** Actionable checklist with specific fixes, not vague suggestions.

**Test it:**
```
/api-docs-audit
Audit our POST /users endpoint documentation
```

Full skill: [`skills/api-docs-audit/SKILL.md`](../skills/api-docs-audit/SKILL.md)

## Skill 2: Code Example Generator

Generates working code in multiple languages (curl, JS, Python, Go).

```bash
mkdir -p ~/.claude/skills/code-examples
```

**Every example includes:**
1. Installation command
2. Complete code with imports
3. Expected output

**Language conventions:**
- cURL: `-X`, `-H`, `-d` flags, `\` line continuation
- JavaScript: ESM imports, async/await, fetch or SDK
- Python: requests or SDK, f-strings, `__main__` block
- Go: full `package main`, `go get`, error checking

**Test it:**
```
/code-examples
Generate examples for creating a user via POST /users
```

Full skill: [`skills/code-examples/SKILL.md`](../skills/code-examples/SKILL.md)

## Skill 3: Developer Newsletter Writer

Writes technical update emails that developers actually read.

```bash
mkdir -p ~/.claude/skills/dev-newsletter
```

**Structure:** Direct subject line → "3 updates this week" → Each update with code + docs link → "Questions? Reply or Discord"

**Newsletter types:**
- Changelog / release notes
- Feature announcements
- Incident postmortems
- Monthly roundups

**Test it:**
```
/dev-newsletter
Write a newsletter announcing webhook retries and a new Python SDK version
```

Full skill: [`skills/dev-newsletter/SKILL.md`](../skills/dev-newsletter/SKILL.md)

## Skill 4: Technical Social Content

Creates developer-focused Twitter threads and LinkedIn posts.

```bash
mkdir -p ~/.claude/skills/tech-social
```

**Twitter thread structure:**
1. Hook (problem or feature)
2. Code example
3. What it does / why it matters
4. Technical detail or edge case
5. Links to docs

**Test it:**
```
/tech-social
Create a Twitter thread announcing automatic webhook retries
```

Full skill: [`skills/tech-social/SKILL.md`](../skills/tech-social/SKILL.md)

## Using all 5 skills together

### Scenario: New API endpoint launch

```
1. /api-docs-audit     → Check existing docs for gaps
2. /code-examples      → Generate examples in 3 languages
3. /technical-tutorial  → Create complete integration guide
4. /dev-newsletter     → Write announcement email
5. /tech-social        → Create Twitter thread for launch
```

**Time without skills:** 12-18 hours
**Time with skills:** 3-4 hours
**Savings:** ~70%

## What you've built

- 5 skills covering the full DevRel content lifecycle
- A repeatable workflow for API feature launches
- A template for creating more skills as needed
- Content that developers will actually read and use
