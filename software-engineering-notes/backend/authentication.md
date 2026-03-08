# Authentication

Authentication verifies user identity. Authorization determines what authenticated users can access.

## Common Methods

### 1. Session-Based Authentication

- Server stores session data after login
- Client receives session ID in cookie
- Stateful: server maintains session state

### 2. JWT (JSON Web Tokens)

- Self-contained token with encoded claims
- Stateless: server doesn't store session
- Consists of: Header.Payload.Signature

```javascript
// JWT structure
{
  "header": { "alg": "HS256", "typ": "JWT" },
  "payload": { "userId": 123, "exp": 1234567890 },
  "signature": "HMACSHA256(header + payload, secret)"
}
```

### 3. OAuth 2.0

- Delegated authorization framework
- Used for "Login with Google/GitHub"
- Issues access tokens for third-party access

## JWT Implementation Example

```javascript
// Node.js with jsonwebtoken
const jwt = require("jsonwebtoken");

// Generate token
const token = jwt.sign(
  { userId: user.id, role: user.role },
  process.env.JWT_SECRET,
  { expiresIn: "24h" },
);

// Verify token (middleware)
const verifyToken = (req, res, next) => {
  const token = req.headers.authorization?.split(" ")[1];
  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    req.user = decoded;
    next();
  } catch (err) {
    res.status(401).json({ error: "Invalid token" });
  }
};
```

## Best Practices

- Always hash passwords (bcrypt, argon2)
- Use HTTPS to protect tokens in transit
- Set appropriate token expiration times
- Implement refresh token rotation
- Store secrets in environment variables
- Never expose sensitive data in JWT payload
