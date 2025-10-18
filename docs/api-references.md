# API References

Matrix Client-Server API reference.

## Authentication

```http
POST /_matrix/client/v3/login
```

## Rooms

```http
POST /_matrix/client/v3/createRoom
POST /_matrix/client/v3/rooms/{roomId}/join
POST /_matrix/client/v3/rooms/{roomId}/leave
```

## Messages

```http
PUT /_matrix/client/v3/rooms/{roomId}/send/m.room.message/{txnId}
GET /_matrix/client/v3/rooms/{roomId}/messages
```

## Sync

```http
GET /_matrix/client/v3/sync
```

## Resources

- [Matrix Client-Server API Spec](https://spec.matrix.org/latest/client-server-api/)
- [API Playground](https://spec.matrix.org/unstable/api-viewer/)

Add your API notes here.
