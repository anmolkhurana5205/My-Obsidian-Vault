### What is Middleware in Next.js?
**Middleware = Code that runs _before_ a request reaches your route, page, or API.**  
It's used for:
- Authentication
- Authorization (role-based access)
- Redirects
- Rewriting URLs
- Logging / analytics
- Blocking requests
- Rate-limiting
- Geo-based routing
It runs in the **Edge Runtime** → extremely fast, low latency.

### Where middleware lives
You create **one file**:
```
middleware.ts
```

in the root of your Next.js project.
Next.js automatically executes it for **every request that matches your config**.

### Simple Example
```
import { NextResponse } from "next/server";

export function middleware(req) {
  const isLoggedIn = false;

  if (!isLoggedIn) {
    return NextResponse.redirect(new URL("/login", req.url));
  }

  return NextResponse.next();
}
```
This runs **before** the page loads and redirects the user to `/login` if they are not authenticated.

### How Middleware Works Internally
```
Request → middleware.ts → route is allowed? → page/API route
```
Middleware can:
- Allow request → `NextResponse.next()`
- Redirect request → `NextResponse.redirect()`
- Rewrite request → `NextResponse.rewrite()`
- Block request → return any response

### Key Features of Middleware
#### 1. Runs on the Edge Runtime
Meaning:
- Very fast
- Doesn't use Node APIs (`fs`, `path`, etc.)
- Uses Web APIs like `Request` and `Response`

#### 2. Can Modify Request / Response
Middleware can change:
- Headers
- URL
- Cookies
- Query params

Example:
```
const res = NextResponse.next();
res.headers.set("x-custom", "hello");
return res;
```

#### 3. Supports Matchers
Control which routes middleware applies to:
```
export const config = {
  matcher: ["/dashboard/:path*", "/profile/:path*"],
};
```

Or apply globally:
```
export const config = {
  matcher: ["/((?!api|_next/static|_next/image|favicon.ico).*)"],
};
```

### # Common Use Cases (Real-world)
#### 1. **Authentication check**
Redirect unauthenticated users:
```
import { NextResponse } from "next/server";

export function middleware(req) {
  const token = req.cookies.get("token");

  if (!token) {
    return NextResponse.redirect(new URL("/login", req.url));
  }

  return NextResponse.next();
}

export const config = {
  matcher: ["/dashboard/:path*"],
};
```

#### 2. **Role-based Access**
```
export function middleware(req) {
  const role = req.cookies.get("role")?.value;

  if (role !== "admin") {
    return NextResponse.redirect(new URL("/not-authorized", req.url));
  }

  return NextResponse.next();
}

export const config = {
  matcher: ["/admin/:path*"],
};
```

#### 3. **Redirect old URLs to new ones**
```
export function middleware(req) {
  if (req.nextUrl.pathname === "/old-home") {
    return NextResponse.redirect(new URL("/new-home", req.url));
  }
}
```

#### 4. **Rewriting URLs**
Rewriting means the user sees the original URL, but the server serves another route.
```
export function middleware(req) {
  const url = req.nextUrl.clone();

  if (url.pathname === "/blog") {
    url.pathname = "/new-blog";
    return NextResponse.rewrite(url);
  }
}
```

#### 5. **Geo-based routing**
```
export function middleware(req) {
  const country = req.geo?.country;

  if (country === "IN") {
    return NextResponse.rewrite(new URL("/india", req.url));
  }

  return NextResponse.next();
}
```

#### 6. **Add/remove headers**
```
export function middleware(req) {
  const res = NextResponse.next();
  res.headers.set("x-powered-by", "NextJS");
  return res;
}
```

### Limitations of Middleware
#### Cannot use:
- Node.js modules (`fs`, `path`)
- Database connections
- Prisma client
- Server components
- Large dependencies
#### Cannot run Long tasks
- It must be fast → Edge optimized.
#### Cannot read request **body**
- Only headers, cookies, URL.

