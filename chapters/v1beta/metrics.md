## Get Total Listens

```http request
GET /metrics/total-listens
```

Retrieves the total amount of listens recorded on wavy.fm. Note that this value is cached for a few seconds.

### Request Headers

- `Authorization` must be a valid access token. No scopes are required for this endpoint.

### Response Body

This endpoint returns JSON. There is no object returned, only the integer (the total listens on wavy.fm).

### Errors

| HTTP Status | Name                         | Code            | Detail Field | Description                             |
| ----------- | ---------------------------- | --------------- | ------------ | --------------------------------------- |
| 401         | Unauthorized                 |                 |              | No access token was provided            |
| 401         | Invalid authorization header |                 |              | The `Authorization` header is malformed |
| 401         | Access token is invalid      | `token.invalid` |              | The given access token is invalid       |
| 401         | Access token is expired      | `token.expired` |              | The given access token has expired      |

## Get Total Users

```http request
GET /metrics/total-users
```

Retrieves the total amount of registered users on wavy.fm. Note that this value is cached for a few seconds.

### Request Headers

- `Authorization` must be a valid access token. No scopes are required for this endpoint.

### Response Body

This endpoint returns JSON. There is no object returned, only the integer (the total users on wavy.fm).

### Errors

| HTTP Status | Name                         | Code            | Detail Field | Description                             |
| ----------- | ---------------------------- | --------------- | ------------ | --------------------------------------- |
| 401         | Unauthorized                 |                 |              | No access token was provided            |
| 401         | Invalid authorization header |                 |              | The `Authorization` header is malformed |
| 401         | Access token is invalid      | `token.invalid` |              | The given access token is invalid       |
| 401         | Access token is expired      | `token.expired` |              | The given access token has expired      |

## Get Global Listens Leaderboard

```http request
GET /metrics/user-listens-leaderboard
```

Retrieves the leaderboard of the top 10 users by listen count. Note that this endpoint is cached for a few minutes.

### Request Headers

- `Authorization` must be a valid access token. No scopes are required for this endpoint.

### Response Body

An array of JSON objects is returned, each with the following structure:

| Field      | Type    | Description              |
| ---------- | ------- | ------------------------ |
| `id`       | string  | wavy.fm user ID (UUID)   |
| `username` | string  | wavy.fm username         |
| `count`    | integer | The user's total listens |

### Errors

| HTTP Status | Name                         | Code            | Detail Field | Description                             |
| ----------- | ---------------------------- | --------------- | ------------ | --------------------------------------- |
| 401         | Unauthorized                 |                 |              | No access token was provided            |
| 401         | Invalid authorization header |                 |              | The `Authorization` header is malformed |
| 401         | Access token is invalid      | `token.invalid` |              | The given access token is invalid       |
| 401         | Access token is expired      | `token.expired` |              | The given access token has expired      |
