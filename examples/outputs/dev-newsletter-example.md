# Example Output: dev-newsletter

**Prompt used:**
```
/dev-newsletter
Write a newsletter announcing:
1. New POST /v2/bulk-import endpoint (up to 10K records, 2.3s average)
2. Python SDK 3.1 with bulk import support
3. Known issue: Rate limiting returns 500 instead of 429 (fix shipping next week)
```

---

**Subject:** New: Bulk import endpoint + Python SDK 3.1

Hey developers,

Three updates this week:

**1. New endpoint: POST /v2/bulk-import**

Import up to 10,000 records in a single request. Average processing time: 2.3 seconds for 5,000 records.

```javascript
const response = await fetch('https://api.example.com/v2/bulk-import', {
  method: 'POST',
  headers: {
    'Authorization': `Bearer ${API_KEY}`,
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    records: [
      { name: 'Jane Smith', email: 'jane@example.com' },
      { name: 'Alex Chen', email: 'alex@example.com' }
    ]
  })
});

const result = await response.json();
console.log(`Imported: ${result.imported}, Failed: ${result.failed.length}`);
```

Rate limit: 10 requests per minute. Max payload: 5MB.

Docs: [link] | Tutorial: [link]

**2. Python SDK 3.1 released**

Adds `client.bulk_import()` with automatic chunking for datasets over 10K records.

```bash
pip install --upgrade yourapi-sdk
```

```python
from yourapi import Client

client = Client(api_key=os.environ["API_KEY"])
result = client.bulk_import(records)  # Auto-chunks if > 10K
print(f"Imported: {result.imported}")
```

Changelog: [link]

**3. Known issue: Rate limit returns 500 instead of 429**

If you hit the rate limit on /v2/ endpoints, you'll get a 500 error instead of 429. We're shipping the fix next week.

Workaround: Check the `X-RateLimit-Remaining` header before making requests.

Tracking issue: [link]

---

Questions? Reply to this email or join us on Discord: [link]
