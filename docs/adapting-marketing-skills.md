# Adapting Marketing Skills for Developer Audiences

A guide for converting any marketing-focused AI skill into a DevRel skill.

## The core shift

| Dimension | Marketing | DevRel |
|---|---|---|
| Goal | Convert | Educate |
| Leads with | Benefits | Working code |
| Tone | Persuasive | Technical |
| Examples | Optional | Required and complete |
| Honesty | Selective | Includes limitations |
| CTA | "Sign up now" | "Read the docs" |

## Adaptation process

### 1. Replace the role definition

**Before:**
> You are an expert copywriter who creates compelling, conversion-focused content.

**After:**
> You are an expert technical writer who creates clear, accurate tutorials that developers can follow to implement a feature.

### 2. Change the voice guidelines

**Remove these words entirely:**
- Revolutionary, game-changing, innovative
- Seamless, streamlined, effortless
- Leverage, unlock, empower, transform
- Cutting-edge, next-generation, best-in-class

**Replace with:**
- Direct technical descriptions
- Specific numbers and benchmarks
- Concrete implementation details

### 3. Add code requirements

Every DevRel skill should require:
- Complete, runnable code examples
- Import statements included
- Error handling shown
- Environment variables for secrets
- Expected output documented

### 4. Restructure the output format

**Marketing format:**
1. Headline (benefit)
2. Subhead (supporting benefit)
3. Body (features)
4. CTA (sign up)

**DevRel format:**
1. What it does (1 sentence)
2. Working code example
3. Step-by-step explanation
4. Error handling
5. Links to docs

### 5. Update the examples

Replace all before/after examples with developer-appropriate ones. Show what bad developer content looks like and what good developer content looks like.

## Checklist for any skill adaptation

- [ ] Role definition says "technical writer" not "copywriter"
- [ ] Banned words list includes marketing buzzwords
- [ ] Code examples are required, not optional
- [ ] Output structure leads with code
- [ ] Examples show developer-appropriate content
- [ ] Voice guidelines specify direct, technical tone
- [ ] Error handling and edge cases are covered
- [ ] Prerequisites section is part of the template
- [ ] Links go to docs, not landing pages

## What Anthropic's growth team learned

Key takeaways applicable to DevRel:

1. **Identify API-enabled repetitive tasks** — For DevRel: GitHub, docs platforms, code repos
2. **Break workflows into specialized sub-agents** — Research → Planning → Writing → Review
3. **Brainstorm and prompt plan before coding** — Spend time upfront with Claude.ai designing the workflow
4. **Results:** 87% time reduction on ad copy (similar gains possible for DevRel content)
