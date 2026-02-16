# Example Output: technical-tutorial

**Prompt used:**
```
/technical-tutorial
Write a tutorial for adding OAuth 2.0 authentication to a Next.js app.
Target audience: Frontend developers familiar with React but new to OAuth.
```

---

## Add OAuth 2.0 Authentication to Your Next.js App in 15 Minutes

### Prerequisites

Before you begin, you'll need:

- Node.js 18 or later
- A Next.js 14+ project (App Router)
- An API key from your OAuth provider ([get one here])
- Basic knowledge of React hooks
- 15 minutes

### Complete working example

Here's the full authentication flow. We'll break it down step by step below.

```typescript
// app/api/auth/login/route.ts
import { NextResponse } from 'next/server';
import { AuthClient } from '@yourapi/auth';

const client = new AuthClient({
  clientId: process.env.AUTH_CLIENT_ID!,
  clientSecret: process.env.AUTH_CLIENT_SECRET!,
  redirectUri: `${process.env.NEXT_PUBLIC_APP_URL}/api/auth/callback`
});

export async function GET() {
  const authUrl = client.getAuthorizationUrl({
    scope: ['read:user', 'write:data'],
    state: crypto.randomUUID() // CSRF protection
  });

  return NextResponse.redirect(authUrl);
}
```

```typescript
// app/api/auth/callback/route.ts
import { NextRequest, NextResponse } from 'next/server';
import { AuthClient } from '@yourapi/auth';
import { cookies } from 'next/headers';

const client = new AuthClient({
  clientId: process.env.AUTH_CLIENT_ID!,
  clientSecret: process.env.AUTH_CLIENT_SECRET!,
  redirectUri: `${process.env.NEXT_PUBLIC_APP_URL}/api/auth/callback`
});

export async function GET(request: NextRequest) {
  const code = request.nextUrl.searchParams.get('code');

  if (!code) {
    return NextResponse.redirect('/login?error=no_code');
  }

  try {
    const tokens = await client.exchangeCode(code);

    cookies().set('access_token', tokens.accessToken, {
      httpOnly: true,
      secure: process.env.NODE_ENV === 'production',
      sameSite: 'lax',
      maxAge: tokens.expiresIn
    });

    return NextResponse.redirect('/dashboard');
  } catch (error) {
    console.error('Token exchange failed:', error);
    return NextResponse.redirect('/login?error=exchange_failed');
  }
}
```

### Step 1: Install the SDK

```bash
npm install @yourapi/auth
```

### Step 2: Set up environment variables

Create `.env.local`:

```bash
AUTH_CLIENT_ID=your_client_id_here
AUTH_CLIENT_SECRET=your_client_secret_here
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

### Step 3: Create the login route

The login route generates an OAuth authorization URL and redirects the user:

```typescript
// app/api/auth/login/route.ts
import { NextResponse } from 'next/server';
import { AuthClient } from '@yourapi/auth';

const client = new AuthClient({
  clientId: process.env.AUTH_CLIENT_ID!,
  clientSecret: process.env.AUTH_CLIENT_SECRET!,
  redirectUri: `${process.env.NEXT_PUBLIC_APP_URL}/api/auth/callback`
});

export async function GET() {
  const authUrl = client.getAuthorizationUrl({
    scope: ['read:user', 'write:data'],
    state: crypto.randomUUID()
  });

  return NextResponse.redirect(authUrl);
}
```

The `state` parameter prevents CSRF attacks. The OAuth provider will return this value in the callback so you can verify the request originated from your app.

### Step 4: Handle the callback

After the user authenticates, the provider redirects back to your callback URL with an authorization code:

```typescript
// app/api/auth/callback/route.ts
import { NextRequest, NextResponse } from 'next/server';
import { AuthClient } from '@yourapi/auth';
import { cookies } from 'next/headers';

const client = new AuthClient({
  clientId: process.env.AUTH_CLIENT_ID!,
  clientSecret: process.env.AUTH_CLIENT_SECRET!,
  redirectUri: `${process.env.NEXT_PUBLIC_APP_URL}/api/auth/callback`
});

export async function GET(request: NextRequest) {
  const code = request.nextUrl.searchParams.get('code');

  if (!code) {
    return NextResponse.redirect('/login?error=no_code');
  }

  try {
    const tokens = await client.exchangeCode(code);

    cookies().set('access_token', tokens.accessToken, {
      httpOnly: true,
      secure: process.env.NODE_ENV === 'production',
      sameSite: 'lax',
      maxAge: tokens.expiresIn
    });

    return NextResponse.redirect('/dashboard');
  } catch (error) {
    console.error('Token exchange failed:', error);
    return NextResponse.redirect('/login?error=exchange_failed');
  }
}
```

The token is stored in an httpOnly cookie — not accessible to JavaScript, which prevents XSS attacks.

### Step 5: Add a login button

```typescript
// app/components/LoginButton.tsx
export function LoginButton() {
  return (
    <a href="/api/auth/login">
      Sign in with OAuth
    </a>
  );
}
```

### Step 6: Protect routes with middleware

```typescript
// middleware.ts
import { NextRequest, NextResponse } from 'next/server';

export function middleware(request: NextRequest) {
  const token = request.cookies.get('access_token');

  if (!token) {
    return NextResponse.redirect(new URL('/login', request.url));
  }

  return NextResponse.next();
}

export const config = {
  matcher: ['/dashboard/:path*', '/settings/:path*']
};
```

### Common errors

**Error: "Invalid client_id"**
- Cause: Your `AUTH_CLIENT_ID` is incorrect or the app isn't registered
- Solution: Verify your credentials at [dashboard link]

**Error: "Redirect URI mismatch"**
- Cause: The callback URL doesn't match what's registered with the provider
- Solution: Add `http://localhost:3000/api/auth/callback` to your registered redirect URIs

**Error: "Token exchange failed"**
- Cause: The authorization code expired (codes are single-use and short-lived)
- Solution: Redirect the user back to `/api/auth/login` to start the flow again

### Next steps

- [Handling refresh tokens](link)
- [Adding role-based access control](link)
- [Example app on GitHub](link)
