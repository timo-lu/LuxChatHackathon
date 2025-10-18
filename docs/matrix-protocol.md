# Matrix Protocol

## Overview

Matrix is an open standard for interoperable, decentralized, real-time communication over the Internet.

## Architecture

### High-Level Components

```
┌─────────────┐         ┌─────────────┐         ┌─────────────┐
│   Client    │ ←─────→ │ Homeserver  │ ←─────→ │ Homeserver  │
│  (LuxChat)  │         │   (Local)   │         │  (Remote)   │
└─────────────┘         └─────────────┘         └─────────────┘
```

### Key Concepts

#### 1. Homeservers
- Each user account is hosted on a homeserver
- Homeservers federate to share messages across the network
- Users are identified as `@username:homeserver.com`

#### 2. Rooms
- Virtual spaces where users communicate
- Identified by room IDs (e.g., `!roomid:homeserver.com`)
- Can be encrypted or unencrypted
- Support various room types (chat, space, etc.)

#### 3. Events
All actions in Matrix are represented as events:
- **Message events**: `m.room.message`, `m.room.encrypted`
- **State events**: `m.room.name`, `m.room.topic`, `m.room.member`
- **Ephemeral events**: `m.typing`, `m.receipt`

## Client-Server API

### Authentication

```
POST /_matrix/client/v3/login
{
  "type": "m.login.password",
  "identifier": {
    "type": "m.id.user",
    "user": "username"
  },
  "password": "password"
}
```

### Sending Messages

```
PUT /_matrix/client/v3/rooms/{roomId}/send/m.room.message/{txnId}
{
  "msgtype": "m.text",
  "body": "Hello, World!"
}
```

### Syncing

The sync endpoint is the primary way clients receive updates:

```
GET /_matrix/client/v3/sync?since={since_token}&timeout=30000
```

## End-to-End Encryption

Matrix supports end-to-end encryption (E2EE) using the Olm and Megolm cryptographic ratchets.

### Key Concepts

- **Device Keys**: Each device has its own cryptographic identity
- **One-time Keys**: Used for establishing secure sessions
- **Room Keys**: Shared session keys for encrypted rooms
- **Key Backup**: Secure storage for recovering encrypted messages

## Federation

Homeservers communicate using the Server-Server API to:
- Share room history
- Propagate events
- Maintain consistency across the network

```
┌──────────────┐                    ┌──────────────┐
│ Homeserver A │ ← Federation API → │ Homeserver B │
│  (alice.com) │                    │   (bob.com)  │
└──────────────┘                    └──────────────┘
```

## Room State Resolution

When conflicting state events occur (e.g., during network splits), Matrix uses a state resolution algorithm to determine the canonical room state.

## Useful Resources

### Official Documentation
- [Matrix Specification](https://spec.matrix.org/)
- [Client-Server API Spec](https://spec.matrix.org/latest/client-server-api/)
- [Server-Server API Spec](https://spec.matrix.org/latest/server-server-api/)

### Learning Resources
- [Matrix.org How It Works](https://matrix.org/docs/guides/introduction)
- [Matrix Architecture Guide](https://matrix.org/docs/guides/core-architecture)
- [Understanding Matrix](https://matrix.org/docs/matrix-concepts/)

### Developer Tools
- [Matrix Developer Portal](https://matrix.org/docs/develop)
- [Try Matrix Now](https://app.element.io/) - Official web client
- [Matrix Public Homeserver List](https://servers.joinmatrix.org/)

## Implementation Considerations

### For LuxChat Development

1. **Choose a Matrix SDK**
   - matrix-js-sdk (JavaScript/TypeScript)
   - matrix-rust-sdk (Rust)
   - matrix-android-sdk2 (Android/Kotlin)
   - matrix-ios-sdk (iOS/Swift)

2. **Handle Sync Loop**
   - Implement efficient sync processing
   - Store sync tokens for resumption
   - Handle rate limiting

3. **Implement E2EE Properly**
   - Verify device keys
   - Handle key backup/restore
   - Implement cross-signing

4. **Optimize Performance**
   - Cache room state
   - Lazy-load room members
   - Implement pagination

## Common Patterns

### Joining a Room

```
POST /_matrix/client/v3/join/{roomIdOrAlias}
```

### Creating a Room

```
POST /_matrix/client/v3/createRoom
{
  "name": "My Room",
  "topic": "A place to chat",
  "preset": "private_chat"
}
```

### Reading Messages

Messages are received through the sync endpoint and stored in the timeline:

```json
{
  "rooms": {
    "join": {
      "!roomId:server.com": {
        "timeline": {
          "events": [
            {
              "type": "m.room.message",
              "content": {
                "msgtype": "m.text",
                "body": "Hello!"
              },
              "sender": "@user:server.com",
              "event_id": "$eventId",
              "origin_server_ts": 1234567890
            }
          ]
        }
      }
    }
  }
}
```

## Next Steps

- Explore [LuxChat Architecture](./luxchat-architecture.md)
- Review [API References](./api-references.md)
- Check out [Development Setup](./development-setup.md)
