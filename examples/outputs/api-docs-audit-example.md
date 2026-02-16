# Example Output: api-docs-audit

**Prompt used:**
```
/api-docs-audit
Audit the POST /v2/users endpoint documentation. Here's what we currently have:

Endpoint: POST /v2/users
Description: Creates a new user
Body: { name: string, email: string }
Response: 201 Created
```

---

## Audit Results for POST /v2/users

### Complete
- HTTP method and path documented
- Basic request body fields listed

### Issues Found

1. **No authentication documentation** — Which auth method? Bearer token? API key? What scopes are required?

2. **Incomplete request body** — Only `name` and `email` listed. Are these required? Are there optional fields? What are the validation rules?
   - Max length for `name`?
   - Email format validation?
   - Are there other accepted fields (e.g., `metadata`, `role`)?

3. **No response body shown** — 201 status code is listed but the response JSON is missing. Developers need to know what fields come back (id, created_at, etc.)

4. **Missing error responses**
   - 400 Bad Request — What validation errors look like
   - 401 Unauthorized — Auth failure response
   - 409 Conflict — Duplicate email handling
   - 422 Unprocessable Entity — Invalid field values
   - 429 Too Many Requests — Rate limit response

5. **No rate limit information** — How many requests per minute? Per API key or per IP?

6. **No code examples** — Zero examples in any language

7. **No content type specified** — `application/json`? `multipart/form-data`?

### Recommendations

1. **Add authentication section:**
   ```
   Authentication: Bearer token required
   Scope: users:write
   Header: Authorization: Bearer YOUR_API_KEY
   ```

2. **Document all request fields with types and constraints:**
   ```
   | Field  | Type   | Required | Constraints          |
   |--------|--------|----------|----------------------|
   | name   | string | yes      | 1-255 characters     |
   | email  | string | yes      | Valid email, unique   |
   | role   | string | no       | "admin" or "member"  |
   ```

3. **Add complete response example:**
   ```json
   {
     "id": "usr_abc123",
     "name": "Jane Smith",
     "email": "jane@example.com",
     "role": "member",
     "created_at": "2024-01-15T10:30:00Z"
   }
   ```

4. **Add error response examples** for 400, 401, 409, 422, 429

5. **Add rate limit info:** `X-RateLimit-Limit: 100` per minute

6. **Add code examples in cURL, JavaScript, and Python** (see `code-examples` skill)

7. **Add idempotency note** — Can the same email be submitted twice? What happens?

### Audit Score: Incomplete

Missing critical sections: authentication, response body, error codes, rate limits, and code examples. Estimated effort to fix: 2-3 hours.
