# Why Developer Marketing Breaks Traditional Marketing Automation

> Part 1 of the DevRel Skills series

## The problem

Most marketing automation tools including AI-powered ones are optimized for **conversion**. They move someone from awareness to consideration to purchase.

That works for B2C but developer audiences operate differently.

### What generic AI produces:

> "Unlock the power of our revolutionary API! Streamline your workflow and leverage cutting-edge technology to transform your business. Join thousands of satisfied customers!"

### What developers actually want:

> New endpoint: `POST /v2/bulk-import`
> Import up to 10,000 records per request. Average processing time: 2.3 seconds.
>
> ```javascript
> const response = await fetch('https://api.example.com/v2/bulk-import', {
>   method: 'POST',
>   headers: { 'Authorization': `Bearer ${API_KEY}` },
>   body: JSON.stringify({ records: data })
> });
> ```

The first one sells. The second one **teaches**. Teaching is what developer marketing is about.

## What makes developer marketing different

| Principle | Traditional Marketing | Developer Marketing |
|---|---|---|
| Structure | Benefit → Feature → How → CTA | Working code → Why it matters → Learn more |
| Approach | "Our API is the fastest!" | [benchmark: 50ms p99 latency] "Here's how" |
| Audience | Explain like they're five | Assume they can code |
| Examples | Snippets are fine | Must be complete and copy-pastable |
| Honesty | Only talk about benefits | Address trade-offs and limitations |

## The DevRel automation gap

A typical API feature launch requires:

| Task | Hours |
|---|---|
| Writing documentation | 4-6 |
| Creating tutorials and examples | 3-4 |
| Announcement content | 2-3 |
| Social distribution | 1-2 |
| Building sample app | 2-3 |
| **Total** | **12-18** |

Most developer tools ship multiple features per month. This doesn't scale manually.

## The solution: Skills adapted for developers

[marketingskills](https://github.com/coreyhaines31/marketingskills) by Corey Haines provides 25 AI skills for marketing. The concept is right with detailed instruction files that teach Claude how to handle specific tasks.

The problem: they're built for traditional marketing. So we adapted them for DevRel.

### Skills audit results

**Use as-is (5):** analytics-tracking, seo-audit, schema-markup, ab-test-setup, marketing-psychology

**Adapt for DevRel (8):** copywriting, content-strategy, email-sequence, social-content, page-cro, competitor-alternatives, product-marketing-context, launch-strategy

**Skip for DevRel (7):** popup-cro, paid-ads, paywall-upgrade-cro, signup-flow-cro, form-cro, pricing-strategy, referral-program

**Build from scratch (5):** technical-tutorial, api-docs-audit, code-examples, dev-newsletter, tech-social

## Getting started

### Install marketingskills (base)

```bash
npx skills add coreyhaines31/marketingskills
```

### Install devrelskills (this repo)

```bash
cp -r skills/* ~/.claude/skills/
```

### Test it

```
/technical-tutorial
Write a tutorial for adding authentication to a Next.js app
```

You should get code-first output with prerequisites, working examples, error handling, and next steps.

---

Next: [Part 2 — Building the Technical Tutorial Skill](02-building-technical-tutorial-skill.md)
