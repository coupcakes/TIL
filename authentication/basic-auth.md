# Basic Authentication

- Most "basic" form of authentication
- Authenticate access to resources over HTTP
- Credentials are sent in request headers

```
Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=
```

- Header consists of `Basic` and a base64 encoded string with `<username>:<password>`
- Not secure as it can be decoded and captured via HTTP

![image](./media/wireshark-basic-auth.png)

- If using, should use HTTPs

## Steps

1. Client tries to access some protected URL
2. Server responds with a 401 message with `WWW-Authenticate` header with a value of `Basic realm="something"`

```javascript
const b64auth = (req.headers.authorization || "").split(" ")[1] || "";
const [login, password] = Buffer.from(b64auth, "base64").toString().split(":");
res.setHeader("WWW-Authenticate", 'Basic realm="ok lol"');
res.writeHead(401, { "Content-Type": "text/plain" });
res.end("okkokokok");
```

3. This prompts the browser alert dialog for the user to enter a username and a password.
4. When the user submits the credentials, the browser encodes them using base64 and sends it in the next request via the Authorization header.
