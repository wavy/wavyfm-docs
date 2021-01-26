## Token

```http request
POST /token
```

Requests a new access token. Query parameter and header values depend on the authentication flow used. This endpoint
should respect the [OAuth 2.0 spec](https://tools.ietf.org/html/rfc6749#section-3.2).

### Form Data

- `grant_type` must be set to `client_credentials`

### Request Headers

- `Content-Type` must be set to `application/x-www-form-urlencoded`
- `Authorization` must be set to `Basic base64(CLIENT_ID:CLIENT_SECRET)`

### Response Body

This endpoint returns JSON. The schema depends on the `grant_type` used in the form:

#### grant_type=client_credentials

| Field          | Type    | Description                                                             |
| -------------- | ------- | ----------------------------------------------------------------------- |
| `access_token` | string  | Temporary and non-refreshable access token with no authorization scopes |
| `token_type`   | string  | Always `bearer`                                                         |
| `expires_in`   | integer | Expiration in seconds (typically `3600`)                                |

### Errors

| HTTP Status | Name                         | Code                  | Detail Field | Description                                                         |
| ----------- | ---------------------------- | --------------------- | ------------ | ------------------------------------------------------------------- |
| 400         | Malformed request            | `auth.invalid`        |              | The wrong authentication method was used for the given `grant_type` |
| 400         | Malformed request            | `grant_type.invalid`  |              | The `grant_type` is invalid or unsupported                          |
| 401         | Invalid authorization header |                       |              | The `Authorization` header is malformed                             |
| 401         | Invalid client credentials   | `credentials.invalid` |              | The given credentials (Client ID and Client Secret) are invalid     |
