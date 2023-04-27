# Session Based Authentication

- Stateful - stores session ID on client and sends it along with each request to the server

## Steps

1. Client sends a login request
2. Server validates the credentials. If valid, the server creates a session and stores it in memory, which is assigned to a user. The session ID is returned to the client.
3. The client receives the session ID and stores it in a cookie if cookies are enabled by the client. If not enabled, the session ID can be stored in local/session storage.
4. Client sends session ID along with each request.
5. Server checks to see if session ID matches any in its storage. If so, it returns the expected data. Else it returns a 401.
6. When the user logs out, the session is destroyed (cookie removed and session removed from the server). The same session ID cannot be reused.
