## Error Format

Errors are returned as a JSON object with the following properties:

#### Error Structure

| Field  | Type               | Description                                                                 |
| ------ | ------------------ | --------------------------------------------------------------------------- |
| status | integer            | HTTP status code.                                                           |
| code   | nullable string    | An optional code relative to the current endpoint. May be null.             |
| name   | string             | A human-readable string describing the type of error.                       |
| detail | nullable, _varies_ | Additional metadata about the error. May be `null`, or any valid JSON type. |

#### Error Example

```json
{
  "status": 404,
  "code": "profile.unknown-identifier",
  "name": "Unknown Profile Identifier",
  "detail": "wavy:id:example"
}
```

## HTTP Status Codes

This is a list of HTTP status codes used by the wavy.fm API.
You should refer to an [external source](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for an exhaustive
list of standard HTTP status codes.

| Code | Category     | Description                                                                                                       |
| ---- | ------------ | ----------------------------------------------------------------------------------------------------------------- |
| 200  | Success      | The request has succeeded. The meaning may be depend on the HTTP method used.                                     |
| 201  | Success      | The request has succeeded and one or more resources were created.                                                 |
| 204  | Success      | The request has succeeded, but no content is returned. This is typically used when deleting resources.            |
| 302  | Redirect     | The requested endpoint has moved. This is typically used when endpoints are renamed.                              |
| 400  | Client Error | The request body or parameters are malformed for the given endpoint.                                              |
| 401  | Client Error | The request lacks proper authentication for the endpoint or context.                                              |
| 403  | Client Error | The request has proper authentication, but lacks the authorization for the endpoint or context.                   |
| 404  | Client Error | The requested endpoint or resource does not exist, or the request lacks the authorization to access the resource. |
| 405  | Client Error | The request specified an HTTP method not supported for the endpoint.                                              |
| 429  | Client Error | The developer platform is imposing "rate limiting" and requires the client to delay further requests.             |
| 500  | Server Error | The request failed due to a bug in the developer platform.                                                        |
| 503  | Server Error | The developer platform is partially or fully unavailable at the moment.                                           |
