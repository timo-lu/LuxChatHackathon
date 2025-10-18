# API References

## Matrix Client-Server API

### Authentication Endpoints

#### Login

```http
POST /_matrix/client/v3/login
Content-Type: application/json

{
  "type": "m.login.password",
  "identifier": {
    "type": "m.id.user",
    "user": "alice"
  },
  "password": "secret_password"
}
```

**Response:**
```json
{
  "user_id": "@alice:example.com",
  "access_token": "abc123",
  "device_id": "GHTYAJCE",
  "home_server": "example.com"
}
```

#### Logout

```http
POST /_matrix/client/v3/logout
Authorization: Bearer abc123
```

### Room Endpoints

#### Create Room

```http
POST /_matrix/client/v3/createRoom
Authorization: Bearer abc123
Content-Type: application/json

{
  "name": "My Room",
  "topic": "Discussion about something",
  "preset": "private_chat",
  "is_direct": false,
  "invite": ["@bob:example.com"],
  "room_alias_name": "myroom"
}
```

**Response:**
```json
{
  "room_id": "!roomId:example.com"
}
```

#### Join Room

```http
POST /_matrix/client/v3/rooms/{roomId}/join
Authorization: Bearer abc123
```

or by alias:

```http
POST /_matrix/client/v3/join/{roomAlias}
Authorization: Bearer abc123
```

#### Leave Room

```http
POST /_matrix/client/v3/rooms/{roomId}/leave
Authorization: Bearer abc123
```

#### Invite User

```http
POST /_matrix/client/v3/rooms/{roomId}/invite
Authorization: Bearer abc123
Content-Type: application/json

{
  "user_id": "@bob:example.com"
}
```

### Message Endpoints

#### Send Message

```http
PUT /_matrix/client/v3/rooms/{roomId}/send/m.room.message/{txnId}
Authorization: Bearer abc123
Content-Type: application/json

{
  "msgtype": "m.text",
  "body": "Hello, World!"
}
```

**Message Types:**

- `m.text`: Plain text message
- `m.emote`: Emote message (e.g., "* Alice waves")
- `m.notice`: Notice message (e.g., bot notifications)
- `m.image`: Image message
- `m.file`: File attachment
- `m.audio`: Audio message
- `m.video`: Video message
- `m.location`: Location sharing

**Example - Image Message:**
```json
{
  "msgtype": "m.image",
  "body": "filename.jpg",
  "url": "mxc://example.com/FHyPlCeYUSFFxlgbQYZmoEoe",
  "info": {
    "h": 398,
    "w": 394,
    "mimetype": "image/jpeg",
    "size": 31037
  }
}
```

#### Send Formatted Message

```json
{
  "msgtype": "m.text",
  "body": "This is **bold** text",
  "format": "org.matrix.custom.html",
  "formatted_body": "This is <strong>bold</strong> text"
}
```

#### Get Messages (Pagination)

```http
GET /_matrix/client/v3/rooms/{roomId}/messages?from={token}&dir=b&limit=10
Authorization: Bearer abc123
```

Parameters:
- `from`: Pagination token
- `dir`: Direction (`b` for backwards, `f` for forwards)
- `limit`: Number of messages to return

### Sync Endpoint

#### Initial Sync

```http
GET /_matrix/client/v3/sync?timeout=30000
Authorization: Bearer abc123
```

#### Incremental Sync

```http
GET /_matrix/client/v3/sync?since={since_token}&timeout=30000
Authorization: Bearer abc123
```

**Response Structure:**
```json
{
  "next_batch": "s123456_789_0",
  "rooms": {
    "join": {
      "!roomId:example.com": {
        "timeline": {
          "events": [...],
          "limited": false,
          "prev_batch": "t123-456"
        },
        "state": {
          "events": [...]
        },
        "ephemeral": {
          "events": [...]
        },
        "account_data": {
          "events": [...]
        }
      }
    },
    "invite": {},
    "leave": {}
  },
  "presence": {
    "events": [...]
  }
}
```

### User Data Endpoints

#### Get User Profile

```http
GET /_matrix/client/v3/profile/{userId}
```

**Response:**
```json
{
  "displayname": "Alice",
  "avatar_url": "mxc://example.com/abc123"
}
```

#### Set Display Name

```http
PUT /_matrix/client/v3/profile/{userId}/displayname
Authorization: Bearer abc123
Content-Type: application/json

{
  "displayname": "Alice Smith"
}
```

#### Set Avatar

```http
PUT /_matrix/client/v3/profile/{userId}/avatar_url
Authorization: Bearer abc123
Content-Type: application/json

{
  "avatar_url": "mxc://example.com/abc123"
}
```

### Media Endpoints

#### Upload Media

```http
POST /_matrix/media/v3/upload
Authorization: Bearer abc123
Content-Type: image/jpeg

[binary data]
```

**Response:**
```json
{
  "content_uri": "mxc://example.com/AQwafuaFswefuhsfAFAgsw"
}
```

#### Download Media

```http
GET /_matrix/media/v3/download/{serverName}/{mediaId}
```

#### Thumbnail

```http
GET /_matrix/media/v3/thumbnail/{serverName}/{mediaId}?width=128&height=128&method=scale
```

### Presence & Typing

#### Set Presence

```http
PUT /_matrix/client/v3/presence/{userId}/status
Authorization: Bearer abc123
Content-Type: application/json

{
  "presence": "online",
  "status_msg": "Working on the hackathon"
}
```

Presence values: `online`, `offline`, `unavailable`

#### Typing Notification

```http
PUT /_matrix/client/v3/rooms/{roomId}/typing/{userId}
Authorization: Bearer abc123
Content-Type: application/json

{
  "typing": true,
  "timeout": 30000
}
```

### Read Receipts

#### Send Read Receipt

```http
POST /_matrix/client/v3/rooms/{roomId}/receipt/m.read/{eventId}
Authorization: Bearer abc123
```

### Room State

#### Get Room State

```http
GET /_matrix/client/v3/rooms/{roomId}/state
Authorization: Bearer abc123
```

#### Get Specific State Event

```http
GET /_matrix/client/v3/rooms/{roomId}/state/{eventType}/{stateKey}
Authorization: Bearer abc123
```

#### Set Room Name

```http
PUT /_matrix/client/v3/rooms/{roomId}/state/m.room.name
Authorization: Bearer abc123
Content-Type: application/json

{
  "name": "New Room Name"
}
```

#### Set Room Topic

```http
PUT /_matrix/client/v3/rooms/{roomId}/state/m.room.topic
Authorization: Bearer abc123
Content-Type: application/json

{
  "topic": "New room topic"
}
```

### Search

#### Search Messages

```http
POST /_matrix/client/v3/search
Authorization: Bearer abc123
Content-Type: application/json

{
  "search_categories": {
    "room_events": {
      "search_term": "search query",
      "keys": ["content.body"],
      "filter": {
        "rooms": ["!roomId:example.com"]
      }
    }
  }
}
```

## End-to-End Encryption APIs

### Device Management

#### Get Devices

```http
GET /_matrix/client/v3/devices
Authorization: Bearer abc123
```

#### Upload Keys

```http
POST /_matrix/client/v3/keys/upload
Authorization: Bearer abc123
Content-Type: application/json

{
  "device_keys": {
    "user_id": "@alice:example.com",
    "device_id": "ABCDEFGH",
    "algorithms": [
      "m.olm.v1.curve25519-aes-sha2",
      "m.megolm.v1.aes-sha2"
    ],
    "keys": {
      "curve25519:ABCDEFGH": "base64+curve25519+key",
      "ed25519:ABCDEFGH": "base64+ed25519+key"
    },
    "signatures": {
      "@alice:example.com": {
        "ed25519:ABCDEFGH": "base64+signature"
      }
    }
  },
  "one_time_keys": {
    "curve25519:AAAAAA": "base64+key"
  }
}
```

### Room Keys

#### Claim Keys

```http
POST /_matrix/client/v3/keys/claim
Authorization: Bearer abc123
Content-Type: application/json

{
  "one_time_keys": {
    "@bob:example.com": {
      "DEVICEID": "signed_curve25519"
    }
  }
}
```

## Rate Limiting

Matrix API endpoints are subject to rate limiting. The response will include:

```json
{
  "errcode": "M_LIMIT_EXCEEDED",
  "error": "Too many requests",
  "retry_after_ms": 2000
}
```

HTTP Status: `429 Too Many Requests`

## Error Codes

Common error codes:

- `M_FORBIDDEN`: The request was forbidden
- `M_UNKNOWN_TOKEN`: The access token is invalid
- `M_BAD_JSON`: Invalid JSON in request
- `M_NOT_JSON`: Request body is not JSON
- `M_NOT_FOUND`: Resource not found
- `M_LIMIT_EXCEEDED`: Rate limit exceeded
- `M_UNKNOWN`: An unknown error occurred
- `M_UNRECOGNIZED`: The request was unrecognized

## Useful Resources

### Official Documentation
- [Matrix Client-Server API Specification](https://spec.matrix.org/latest/client-server-api/)
- [Matrix API Playground](https://spec.matrix.org/unstable/api-viewer/)

### SDKs
- [matrix-js-sdk](https://github.com/matrix-org/matrix-js-sdk) - JavaScript/TypeScript
- [matrix-rust-sdk](https://github.com/matrix-org/matrix-rust-sdk) - Rust
- [matrix-android-sdk2](https://github.com/matrix-org/matrix-android-sdk2) - Android/Kotlin
- [matrix-ios-sdk](https://github.com/matrix-org/matrix-ios-sdk) - iOS/Swift

### Tools
- [Matrix Spec API Viewer](https://spec.matrix.org/latest/client-server-api/)
- [Postman Collection for Matrix API](https://www.postman.com/matrix-org)

## Next Steps

- Review [Matrix Protocol](./matrix-protocol.md) for concepts
- Check [Development Setup](./development-setup.md) for local testing
- Explore [Tools & Utilities](./tools-and-utilities.md) for helper libraries
