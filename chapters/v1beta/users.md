## Get Profile

```http request
GET /users/{uri}
```

Retrieves the public profile of a wavy.fm user. Note that private profiles will not be returned at all by this endpoint,
regardless of authorization scopes.

### Path Parameters

- The `uri` path parameter must be a [user URI](./overview#user-uris).

### Request Headers

- `Authorization` must be a valid access token. No scopes are required for this endpoint.

### Response Body

This endpoint returns a JSON object with the following structure:

| Field       | Type                       | Description                                       |
| ----------- | -------------------------- | ------------------------------------------------- |
| `id`        | string                     | wavy.fm user ID (UUID)                            |
| `username`  | string                     | wavy.fm username                                  |
| `join_time` | string (RFC3339 timestamp) | The timestamp when the user created their account |
| `profile`   | profile object (see below) | Profile information                               |

#### profile object

| Field          | Type                                | Description                                            |
| -------------- | ----------------------------------- | ------------------------------------------------------ |
| `url`          | string                              | URL to the profile on wavy.fm                          |
| `avatar`       | string                              | URL to the user's avatar                               |
| `avatar_small` | string                              | URL to the user's downscaled avatar                    |
| `country`      | nullable string                     | 2 or 3-character country code                          |
| `biography`    | nullable string                     | The profile's biography                                |
| `twitter`      | nullable string                     | The profile's Twitter username                         |
| `instagram`    | nullable string                     | The profile's Instagram username                       |
| `spotify`      | nullable Spotify object (see below) | The profile's Spotify account, if shown on the profile |
| `discord`      | nullable Discord object (see below) | The profile's Discord account, if shown on the profile |

#### Spotify object

| Field          | Type            | Description          |
| -------------- | --------------- | -------------------- |
| `id`           | string          | Spotify user ID      |
| `display_name` | nullable string | Spotify display name |

#### Discord object

| Field          | Type            | Description                                |
| -------------- | --------------- | ------------------------------------------ |
| `id`           | string          | Discord user ID                            |
| `display_name` | nullable string | Discord username (including discriminator) |

### Errors

| HTTP Status | Name                         | Code              | Detail Field | Description                                             |
| ----------- | ---------------------------- | ----------------- | ------------ | ------------------------------------------------------- |
| 400         | Malformed request            | `uri.invalid`     |              | The given URI is malformed                              |
| 401         | Unauthorized                 |                   |              | No access token was provided                            |
| 401         | Invalid authorization header |                   |              | The `Authorization` header is malformed                 |
| 401         | Access token is invalid      | `token.invalid`   |              | The given access token is invalid                       |
| 401         | Access token is expired      | `token.expired`   |              | The given access token has expired                      |
| 403         | This profile is private      | `profile.private` |              | The requested profile is private and cannot be returned |

## Get Profile History Stats

```http request
GET /users/{uri}/history/stats
```

Retrieves some statistics about the user's history. Note that private profiles will not be returned at all by this endpoint,
regardless of authorization scopes.

### Path Parameters

- The `uri` path parameter must be a [user URI](./overview#user-uris).

### Request Headers

- `Authorization` must be a valid access token. No scopes are required for this endpoint.

### Response Body

This endpoint returns a JSON object with the following structure:

| Field           | Type    | Description                                 |
| --------------- | ------- | ------------------------------------------- |
| `total_listens` | integer | The amount of listens in the user's history |
| `total_artists` | integer | The amount of artists in the user's history |

### Errors

| HTTP Status | Name                         | Code              | Detail Field | Description                                             |
| ----------- | ---------------------------- | ----------------- | ------------ | ------------------------------------------------------- |
| 400         | Malformed request            | `uri.invalid`     |              | The given URI is malformed                              |
| 401         | Unauthorized                 |                   |              | No access token was provided                            |
| 401         | Invalid authorization header |                   |              | The `Authorization` header is malformed                 |
| 401         | Access token is invalid      | `token.invalid`   |              | The given access token is invalid                       |
| 401         | Access token is expired      | `token.expired`   |              | The given access token has expired                      |
| 403         | This profile is private      | `profile.private` |              | The requested profile is private and cannot be returned |

## Get Currently Listening

```http request
GET /users/{uri}/history/current
```

Retrieves the song, album, and artist(s) the user is currently listening to.
Note that private profiles will not be returned at all by this endpoint, regardless of authorization scopes.

Warning: this endpoint is relatively unstable at the moment.

### Path Parameters

- The `uri` path parameter must be a [user URI](./overview#user-uris).

### Request Headers

- `Authorization` must be a valid access token. No scopes are required for this endpoint.

### Response Body

This endpoint returns a JSON object with the following structure:

| Field     | Type                                | Description                                              |
| --------- | ----------------------------------- | -------------------------------------------------------- |
| `local`   | boolean                             | Whether the user is listening to a local file on Spotify |
| `song`    | song object (see below)             | The song being listened to                               |
| `album`   | album object (see below)            | The album being listened to                              |
| `artists` | array of artist objects (see below) | The artists being listened to                            |

#### song object

| Field        | Type            | Description                                                                              |
| ------------ | --------------- | ---------------------------------------------------------------------------------------- |
| `name`       | string          | The title of the song                                                                    |
| `source`     | nullable string | The source identifier for the song. May be null if the user is listening to a local file |
| `source_url` | nullable string | The source URL of the song. May be null if the user is listening to a local file         |

#### album object

| Field        | Type            | Description                                                                               |
| ------------ | --------------- | ----------------------------------------------------------------------------------------- |
| `name`       | string          | The title of the album                                                                    |
| `source`     | nullable string | The source identifier for the album. May be null if the user is listening to a local file |
| `source_url` | nullable string | The source URL of the album. May be null if the user is listening to a local file         |
| `art_url`    | nullable string | Artwork URL for the album. May be null if the user is listening to a local file           |

#### artist object

| Field        | Type            | Description                                                                                |
| ------------ | --------------- | ------------------------------------------------------------------------------------------ |
| `name`       | string          | The name of the artist                                                                     |
| `source`     | nullable string | The source identifier for the artist. May be null if the user is listening to a local file |
| `source_url` | nullable string | The source URL of the artist. May be null if the user is listening to a local file         |

### Errors

| HTTP Status | Name                         | Code              | Detail Field | Description                                             |
| ----------- | ---------------------------- | ----------------- | ------------ | ------------------------------------------------------- |
| 400         | Malformed request            | `uri.invalid`     |              | The given URI is malformed                              |
| 401         | Unauthorized                 |                   |              | No access token was provided                            |
| 401         | Invalid authorization header |                   |              | The `Authorization` header is malformed                 |
| 401         | Access token is invalid      | `token.invalid`   |              | The given access token is invalid                       |
| 401         | Access token is expired      | `token.expired`   |              | The given access token has expired                      |
| 403         | This profile is private      | `profile.private` |              | The requested profile is private and cannot be returned |

## Get Recently Listened

```http request
GET /users/{uri}/history/recent
```

Retrieves the most recent listens recorded by the user.
Note that private profiles will not be returned at all by this endpoint, regardless of authorization scopes.

### Path Parameters

- The `uri` path parameter must be a [user URI](./overview#user-uris).

### Request Headers

- `Authorization` must be a valid access token. No scopes are required for this endpoint.

### Response Body

This endpoint returns a JSON object with the following structure:

| Field     | Type                                | Description                                              |
| --------- | ----------------------------------- | -------------------------------------------------------- |
| `local`   | boolean                             | Whether the user is listening to a local file on Spotify |
| `song`    | song object (see below)             | The song being listened to                               |
| `album`   | album object (see below)            | The album being listened to                              |
| `artists` | array of artist objects (see below) | The artists being listened to                            |

#### listen object

| Field     | Type                                | Description                                           |
| --------- | ----------------------------------- | ----------------------------------------------------- |
| `local`   | boolean                             | Whether the song was a local file. Always `false`     |
| `date`    | string (RFC3339 date-time)          | The timestamp when the listen was registered          |
| `play_id` | string                              | ID for the listen. Note: this is unique per-user only |
| `song`    | song object (see below)             | The song being listened to                            |
| `album`   | album object (see below)            | The album being listened to                           |
| `artists` | array of artist objects (see below) | The artists being listened to                         |

#### song object

| Field        | Type   | Description                        |
| ------------ | ------ | ---------------------------------- |
| `name`       | string | The title of the song              |
| `source`     | string | The source identifier for the song |
| `source_url` | string | The source URL of the song.        |

#### album object

| Field        | Type   | Description                         |
| ------------ | ------ | ----------------------------------- |
| `name`       | string | The title of the album              |
| `source`     | string | The source identifier for the album |
| `source_url` | string | The source URL of the album         |
| `art_url`    | string | Artwork URL for the album           |

#### artist object

| Field        | Type   | Description                          |
| ------------ | ------ | ------------------------------------ |
| `name`       | string | The name of the artist               |
| `source`     | string | The source identifier for the artist |
| `source_url` | string | The source URL of the artist         |

### Errors

| HTTP Status | Name                         | Code              | Detail Field | Description                                             |
| ----------- | ---------------------------- | ----------------- | ------------ | ------------------------------------------------------- |
| 400         | Malformed request            | `uri.invalid`     |              | The given URI is malformed                              |
| 401         | Unauthorized                 |                   |              | No access token was provided                            |
| 401         | Invalid authorization header |                   |              | The `Authorization` header is malformed                 |
| 401         | Access token is invalid      | `token.invalid`   |              | The given access token is invalid                       |
| 401         | Access token is expired      | `token.expired`   |              | The given access token has expired                      |
| 403         | This profile is private      | `profile.private` |              | The requested profile is private and cannot be returned |
