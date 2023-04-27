# Authentication

- [Basic Authentication](./basic-auth.md)
- [Session Based Authentication](./session-based-auth.md)

## Stateful vs. Stateless

- **Stateful**: Authentication session can be revoked, information is stored on server side
- **Stateless**: Authentication session cannot be revoked, information is stored on client side and the server can only verify validity by checking that the payload and signature match
