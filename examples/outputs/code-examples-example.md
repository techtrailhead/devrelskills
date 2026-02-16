# Example Output: code-examples

**Prompt used:**
```
/code-examples
Generate examples for creating a user via POST /v2/users.

Endpoint: POST https://api.example.com/v2/users
Auth: Bearer token
Body: { name: string, email: string, role?: "admin" | "member" }
Response: 201 with user object
```

---

## Create a User

### cURL

```bash
curl -X POST https://api.example.com/v2/users \
  -H "Authorization: Bearer $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Jane Smith",
    "email": "jane@example.com",
    "role": "member"
  }'
```

Response (201 Created):

```json
{
  "id": "usr_abc123",
  "name": "Jane Smith",
  "email": "jane@example.com",
  "role": "member",
  "created_at": "2024-01-15T10:30:00Z"
}
```

### JavaScript (Node.js)

```bash
npm install node-fetch
```

```javascript
import fetch from 'node-fetch';

const API_KEY = process.env.API_KEY;

async function createUser(name, email, role = 'member') {
  const response = await fetch('https://api.example.com/v2/users', {
    method: 'POST',
    headers: {
      'Authorization': `Bearer ${API_KEY}`,
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({ name, email, role })
  });

  if (!response.ok) {
    const error = await response.json();
    throw new Error(`${response.status}: ${error.message}`);
  }

  return response.json();
}

try {
  const user = await createUser('Jane Smith', 'jane@example.com');
  console.log('User created:', user.id);
} catch (error) {
  console.error('Failed to create user:', error.message);
}
```

Expected output:

```
User created: usr_abc123
```

### Python

```bash
pip install requests
```

```python
import os
import requests

API_KEY = os.environ["API_KEY"]

def create_user(name: str, email: str, role: str = "member") -> dict:
    response = requests.post(
        "https://api.example.com/v2/users",
        headers={
            "Authorization": f"Bearer {API_KEY}",
            "Content-Type": "application/json",
        },
        json={"name": name, "email": email, "role": role},
    )
    response.raise_for_status()
    return response.json()


if __name__ == "__main__":
    try:
        user = create_user("Jane Smith", "jane@example.com")
        print(f"User created: {user['id']}")
    except requests.HTTPError as e:
        print(f"Failed to create user: {e.response.status_code} {e.response.text}")
```

Expected output:

```
User created: usr_abc123
```

### Error handling (all languages)

| Status | Meaning | Action |
|---|---|---|
| 400 | Invalid request body | Check required fields and types |
| 401 | Invalid or missing API key | Verify `API_KEY` is set correctly |
| 409 | Email already exists | Use a different email or fetch existing user |
| 429 | Rate limit exceeded | Wait and retry (check `Retry-After` header) |
