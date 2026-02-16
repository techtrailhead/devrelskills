# Example: Complete API Feature Launch Workflow

Use all 5 devrelskills to go from "new endpoint" to "fully launched" in 3-4 hours.

## Scenario

You're launching `POST /v2/bulk-import` — a new endpoint that imports up to 10,000 records per request.

## Step 1: Audit existing docs

```
/api-docs-audit

Audit our /v2/ endpoints. We're adding POST /v2/bulk-import.
Check if existing v2 docs are complete before we add the new endpoint.
```

**Output:** Checklist of gaps in existing docs to fix alongside the new endpoint.

## Step 2: Generate code examples

```
/code-examples

Generate examples for POST /v2/bulk-import.

Endpoint details:
- Method: POST
- URL: https://api.example.com/v2/bulk-import
- Auth: Bearer token
- Body: { records: Array<{id, name, email}> }
- Max records: 10,000
- Rate limit: 10 requests/minute
- Response: { imported: number, failed: Array<{index, error}> }
```

**Output:** Working examples in cURL, JavaScript, and Python.

## Step 3: Write the tutorial

```
/technical-tutorial

Write a tutorial for the new bulk import endpoint.
Target audience: Backend developers integrating our API.
Framework: Node.js with Express.

Cover:
- Basic import (small batch)
- Large import with chunking
- Error handling and retries
- Monitoring import progress
```

**Output:** Complete tutorial with prerequisites, working code, error handling, and next steps.

## Step 4: Draft the newsletter

```
/dev-newsletter

Write a newsletter announcing:
1. New POST /v2/bulk-import endpoint (10K records, 2.3s avg)
2. Python SDK 3.1 with bulk import support
3. New example repo: bulk-import-demo on GitHub
```

**Output:** Scannable email with code snippets and links.

## Step 5: Create social content

```
/tech-social

Create a Twitter thread announcing POST /v2/bulk-import.

Key stats:
- 10,000 records per request
- 2.3 second average processing
- Automatic validation and error reporting
```

**Output:** 5-tweet thread with code examples and links.

## Timeline

| Step | Skill | Time |
|---|---|---|
| Doc audit | `api-docs-audit` | 20 min |
| Code examples | `code-examples` | 30 min |
| Tutorial | `technical-tutorial` | 60 min |
| Newsletter | `dev-newsletter` | 30 min |
| Social | `tech-social` | 20 min |
| **Review & polish** | — | **60 min** |
| **Total** | | **~3.5 hours** |

Compare to 12-18 hours without skills.
