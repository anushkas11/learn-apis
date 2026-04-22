# OAuth 2.0 Documentation

## What is OAuth 2.0?
OAuth 2.0 is an authorization framework that allows third-party applications to obtain limited access to an HTTP service, either on behalf of a resource owner or by allowing the third-party application to obtain access on its own behalf. It is widely used for granting access to APIs and is defined in [RFC 6749](https://tools.ietf.org/html/rfc6749).

## Key Components
1. **Resource Owner**: Typically the user, who owns the data that the third-party application wants to access.
2. **Client**: The application that wants to access the user's data. It may be a web application, a mobile app, or any other type of application.
3. **Resource Server**: The server that holds the user's data, which the client wants to access.
4. **Authorization Server**: The server that authenticates the resource owner and issues access tokens to the client.

## Authorization Flow
The OAuth 2.0 authorization flow typically involves the following steps:
1. **Authorization Request**: The client requests authorization from the resource owner.
2. **Authorization Grant**: If the resource owner approves the request, the client receives an authorization grant.
3. **Access Token Request**: The client sends the authorization grant to the authorization server to request an access token.
4. **Access Token Response**: The authorization server responds with an access token (and optionally a refresh token).
5. **Resource Access**: The client uses the access token to access protected resources on the resource server.

## Node.js Implementation Example with Google
Here's a simple implementation in Node.js that uses Google as the authorization server:

### Prerequisites
- Node.js installed
- Express framework

### Installation
```bash
npm install express passport-google-oauth20 express-session
```

### Code Example
```javascript
const express = require('express');
const passport = require('passport');
const GoogleStrategy = require('passport-google-oauth20').Strategy;
const session = require('express-session');

const app = express();

app.use(session({ secret: 'your_secret_key', resave: false, saveUninitialized: true }));
app.use(passport.initialize());
app.use(passport.session());

passport.use(new GoogleStrategy({
  clientID: 'YOUR_GOOGLE_CLIENT_ID',
  clientSecret: 'YOUR_GOOGLE_CLIENT_SECRET',
  callbackURL: '/auth/google/callback'
}, (accessToken, refreshToken, profile, done) => {
  return done(null, profile);
}));

passport.serializeUser((user, done) => {
  done(null, user);
});

passport.deserializeUser((user, done) => {
  done(null, user);
});

app.get('/auth/google', passport.authenticate('google', { scope: ['profile', 'email'] }));

app.get('/auth/google/callback', passport.authenticate('google', { failureRedirect: '/' }), (req, res) => {
  res.redirect('/');
});

app.get('/', (req, res) => {
  res.send('<h1>Home</h1>');
});

app.listen(3000, () => {
  console.log('Server started on http://localhost:3000');
});
```

## Advantages
- **Delegated Access**: Users can grant limited access to their resources without sharing credentials.
- **Scoped Access**: Clients can access resources within defined scopes, limiting exposure to sensitive data.
- **Token-based Mechanism**: Access tokens can be easily revoked and expire, enhancing security.

## Best Practices
- Use HTTPS to secure the authorization process.
- Validate redirect URIs to prevent unauthorized access.
- Implement proper token storage and expiration handling.
- Regularly review and update permissions granted to clients.

---