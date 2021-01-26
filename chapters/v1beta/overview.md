This chapter includes the reference of the `v1beta` API version. It should be noted that this is a **beta** version, so
endpoints and resources may be sparsely documented. You can learn more about versioning in
the [API Reference](../intro/api).

Since this is the first API version, some endpoints described here are still in development and may be completely
inaccessible. Once the API is deemed complete and documented fully, it will be promoted to `v1`.

All endpoints in this version are under this base URL:

```
https://wavy.fm/api/v1beta
```

## User URIs

In user-related endpoints, a **user URI** selects the user through one of 3 selectors:

- `wavyfm:user:id:<user ID>` to select by wavy.fm user ID (UUID)
- `wavyfm:user:username:<username>` to select by wavy.fm username
- `wavyfm:user:discord:<discord ID>` to select by Discord ID (a large number called 'snowflake')
