# Building Your First DevRel Skill: Technical Tutorial Writer

> Part 2 of the DevRel Skills series

By the end of this tutorial, you'll have a working `technical-tutorial` skill that generates developer-appropriate content with working code examples, technical specifications, and proper documentation structure.

**Time to complete:** 45-60 minutes

## How skills work

A skill is a SKILL.md file that tells Claude:

- When to use this skill (triggers)
- What questions to ask first
- What frameworks and principles to follow
- What good output looks like
- What mistakes to avoid

The skill does the heavy lifting. Claude executes it consistently.

## Step-by-step build

### 1. Create the directory

```bash
mkdir -p ~/.claude/skills/technical-tutorial
```

### 2. Create SKILL.md

The skill file has these sections:

#### Frontmatter (triggers)

```yaml
---
name: technical-tutorial
description: Write technical tutorials and guides for developer audiences.
  Use when creating API documentation, SDK guides, integration tutorials, or
  technical blog posts.
---
```

#### Role definition

Sets Claude's mindset — technical writer, not marketer.

#### Context awareness

Checks for existing files (`.claude/api-reference.md`, `.claude/sdk-examples.md`) before asking redundant questions.

#### Information gathering

5 key questions: what outcome, what language, what prerequisites, what scope, existing samples.

#### Tutorial structure

1. Title (outcome-focused, not feature-focused)
2. Prerequisites box
3. Complete working example first
4. Step-by-step implementation
5. Error handling section
6. Next steps

#### Code quality principles

Every example must be: complete, copy-pastable, tested, commented, error-handled, modern, consistent.

#### Voice and tone

Technical and direct. Never: "revolutionary", "seamless", "leverage", "unlock".

The complete skill file is at [`skills/technical-tutorial/SKILL.md`](../skills/technical-tutorial/SKILL.md).

## Testing your skill

### Test 1: Authentication tutorial

```
/technical-tutorial

Write a tutorial for adding authentication to a Next.js app using
OAuth. Target: frontend devs familiar with React but new to OAuth.
```

**Good signs:** Prerequisites, complete code with imports, step-by-step breakdown, error handling, next steps, developer-appropriate language.

**Red flags:** Marketing language, incomplete snippets, missing error handling, no prerequisites, vague explanations.

### Test 2: API documentation

```
/technical-tutorial

Document the POST /v2/bulk-import endpoint. Accepts array of records
(max 10,000), returns import results. Include rate limits and error codes.
```

**Expected:** Endpoint spec, complete request example, response format, error codes, rate limits, examples in multiple languages.

### Test 3: SDK integration guide

```
/technical-tutorial

Write a guide for integrating our Python SDK into a Flask app.
Show initialization, API calls, and error handling.
```

**Expected:** Installation, imports, configuration, working examples, error handling patterns, best practices.

## Iterating on quality

### Issue: Still too marketing-y

Strengthen the banned words list in SKILL.md:

```
CRITICAL: Never use these words:
- Revolutionary, game-changing, innovative
- Seamless, streamlined, effortless
- Leverage, unlock, empower
```

### Issue: Incomplete code examples

Add emphasis:

```
CODE EXAMPLES MUST BE COMPLETE.
If you write `// ... rest of code`, you're doing it wrong.
```

### Issue: Missing context

Create context files that the skill reads automatically:

```bash
mkdir -p .claude
nano .claude/api-reference.md
```

### Issue: Examples too simple

Add complex examples to SKILL.md showing production-quality patterns (token exchange, refresh handling, error recovery).

## Refinement cycle

1. Test the skill with various prompts
2. Identify patterns in what's not working
3. Update SKILL.md with stronger guidelines
4. Test again
5. Repeat until quality is consistent

---

Next: [Part 3 — Five Essential DevRel Skills](03-five-essential-devrel-skills.md)
