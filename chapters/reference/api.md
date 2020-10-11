The wavy.fm API is a collection of [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer) web services
over the HTTPS protocol. In the future, this API may be extended to support additional protocols including gRPC and
WebSockets.


## Media Type

The API supports a variety of media types. For the vast majority of transactions, JSON (`application/json` MIME type)
is used. All text-based transactions, including JSON, are encoded in UTF-8.

For image-based transactions, endpoints may support one or a combination of the following formats: PNG, JPEG, GIF.

Certain transactions will also support plain text (`text/plain` MIME type).

## Endpoints and Versioning

The entirety of wavy.fm's API is accessible from the `wavy.fm` origin, via the HTTPS protocol (port 443). In addition,
all endpoints (for any version) are prefixed with `/api`. Also, the endpoints will always be prefixed by
the version of the API they are a part of.

```
https://wavy.fm/api/{version}/...
```

For example, the following URL routes to the `/profile` endpoint in the `v1` version of the API:

```
https://wavy.fm/api/v1/profile
```

As of writing, there are 2 versions of the API:

```
https://wavy.fm/api/v1beta
https://wavy.fm/api/internal
```

The `internal` version is reserved for undocumented endpoints with the purpose of enhancing the wavy.fm website. There
may be additional restrictions in the [Developer Terms of Service](../intro/terms) in regards to the Internal version.
For example, you may not be able to develop a certain types of projects using this version.

Finally, the latest version of the API (`v1`) is the recommended one to use in new and existing projects. You should
migrate to new versions as soon as possible to prevent disruptions in your application. While we try to preserve
backward-compatibility, we do not guarantee it.

An exception can be made for versions with the `beta` suffix. Such versions may be sparsely documented and unstable
until they are stabilized in a full release. For example, the `v1beta` version would be the pre-release version of the
future `v1` version.
