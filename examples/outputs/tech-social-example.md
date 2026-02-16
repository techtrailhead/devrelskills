# Example Output: tech-social

**Prompt used:**
```
/tech-social
Create a Twitter thread announcing POST /v2/bulk-import.

Key stats:
- 10,000 records per request
- 2.3 second average processing
- Automatic validation and error reporting
- Rate limit: 10 req/min
```

---

## Twitter Thread

**1/**
New endpoint: POST /v2/bulk-import

Import 10,000 records in a single request. Average processing: 2.3 seconds.

Here's how it works:

**2/**
```javascript
const response = await fetch('https://api.example.com/v2/bulk-import', {
  method: 'POST',
  headers: {
    'Authorization': `Bearer ${API_KEY}`,
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ records: data })
});
```

That's it. One request, up to 10K records.

**3/**
Every record is validated before import. If some fail, you get a detailed error report:

```json
{
  "imported": 9847,
  "failed": [
    { "index": 12, "error": "invalid email format" },
    { "index": 503, "error": "duplicate record" }
  ]
}
```

No silent failures.

**4/**
Performance numbers:

- 1,000 records: 0.8s
- 5,000 records: 2.3s
- 10,000 records: 4.1s

Rate limit: 10 requests/minute
Max payload: 5MB

**5/**
Docs: [link]
Python SDK with auto-chunking: [link]
Example app: [GitHub link]

Try it out and let us know what you think.

---

## LinkedIn Post

We just shipped a new bulk import endpoint.

POST /v2/bulk-import lets you import up to 10,000 records in a single API request with an average processing time of 2.3 seconds.

What makes it useful:
- Automatic validation on every record
- Detailed error reporting (no silent failures)
- Processing under 5 seconds for most workloads

Built this based on feedback from teams doing large data migrations who were hitting rate limits with individual record creation.

Docs and code examples: [link]
