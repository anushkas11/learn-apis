# JWT Authentication

JSON Web Tokens (JWT) are an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed.

## Structure of JWT

A JWT is composed of three parts:
1. **Header**: Contains metadata about the token, typically the type of token (JWT) and the signing algorithm being used (e.g., HMAC SHA256 or RSA).
   Example:
   ```json
   {
     "alg": "HS256",
     "typ": "JWT"
   }
   ```

2. **Payload**: Contains the claims. Claims are statements about an entity (typically, the user) and additional data. There are three types of claims: registered, public, and private.
   Example:
   ```json
   {
     "sub": "1234567890",
     "name": "John Doe",
     "iat": 1516239022
   }
   ```

3. **Signature**: To create the signature part, you have to take the encoded header, encoded payload, a secret, and the algorithm specified in the header. For example: 
   ```bash
   HMACSHA256(
     base64UrlEncode(header) + "." + 
     base64UrlEncode(payload),
     secret)
   ```

### How JWT works
1. The client sends a login request to the server.
2. If the credentials are valid, the server generates a JWT and sends it back to the client.
3. The client stores the JWT (e.g., in local storage or cookies) and includes it in the Authorization header of future requests.
4. The server verifies the token's signature and extracts the user data from the payload to authorize the request.

### Node.js Implementation Example
```javascript
const express = require('express');
const jwt = require('jsonwebtoken');

const app = express();
const PORT = 3000;
const SECRET_KEY = "your_secret_key";

app.use(express.json());

// Route to authenticate user and issue JWT
app.post('/login', (req, res) => {
  // Validate user credentials...
  const token = jwt.sign({ id: user.id }, SECRET_KEY, { expiresIn: '1h' });
  res.json({ token });
});

// Middleware to verify token
function verifyToken(req, res, next) {
  const token = req.headers['authorization'];
  if (!token) return res.sendStatus(403);

  jwt.verify(token, SECRET_KEY, (err, user) => {
    if (err) return res.sendStatus(403);
    req.user = user;
    next();
  });
}

// Protected route
app.get('/protected', verifyToken, (req, res) => {
  res.json({ message: "This is a protected route", user: req.user });
});

app.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
```

### Advantages of JWT
- **Compact**: Can be sent via URL, POST parameter, or in an HTTP header.
- **Self-contained**: Contains all the information about the user, reducing the need to query a database for authentication.
- **Secure**: Since it is signed, the recipient can verify that the sender is who it claims to be and ensure that the message wasn't changed along the way.

### Best Practices
- Use strong secrets and algorithms (e.g., RS256).
- Implement expiration times for tokens to increase security.
- Use HTTPS to prevent token interception.
- Validate the tokens on the server side for every request that requires authentication.