# LuxChat Hackathon - Printable Cheat Sheet

_Print this page for quick reference during development_

---

## Matrix API Endpoints

### Base URL
```
http://localhost:8008/_matrix/client/v3/
```

### Authentication
**Login**: `POST /login`
**Logout**: `POST /logout`

### Rooms
**Create**: `POST /createRoom`
**Join**: `POST /rooms/{roomId}/join`
**Leave**: `POST /rooms/{roomId}/leave`
**Invite**: `POST /rooms/{roomId}/invite`

### Messages
**Send**: `PUT /rooms/{roomId}/send/m.room.message/{txnId}`
**Get History**: `GET /rooms/{roomId}/messages`

### Sync
**Sync**: `GET /sync?since={token}&timeout=30000`

### User Profile
**Get Profile**: `GET /profile/{userId}`
**Set Name**: `PUT /profile/{userId}/displayname`
**Set Avatar**: `PUT /profile/{userId}/avatar_url`

---

## Matrix Identifiers

| Type | Format | Example |
|------|--------|---------|
| User | `@user:server` | `@alice:matrix.org` |
| Room | `!room:server` | `!abc123:matrix.org` |
| Alias | `#alias:server` | `#general:matrix.org` |
| Event | `$event:server` | `$xyz789:matrix.org` |

---

## Common Event Types

| Event Type | Description |
|------------|-------------|
| `m.room.message` | Text message |
| `m.room.encrypted` | Encrypted message |
| `m.room.member` | Membership change |
| `m.room.name` | Room name |
| `m.room.topic` | Room topic |
| `m.typing` | Typing indicator |
| `m.receipt` | Read receipt |

---

## Message Types (msgtype)

| Type | Usage |
|------|-------|
| `m.text` | Plain text |
| `m.emote` | Action/emote |
| `m.notice` | Bot/notice |
| `m.image` | Image |
| `m.file` | File |
| `m.video` | Video |
| `m.audio` | Audio |

---

## HTTP Status Codes

| Code | Meaning |
|------|---------|
| 200 | Success |
| 400 | Bad request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not found |
| 429 | Rate limited |
| 500 | Server error |

---

## Matrix Error Codes

| Code | Description |
|------|-------------|
| `M_FORBIDDEN` | Access forbidden |
| `M_UNKNOWN_TOKEN` | Invalid token |
| `M_BAD_JSON` | Invalid JSON |
| `M_NOT_FOUND` | Not found |
| `M_LIMIT_EXCEEDED` | Rate limited |

---

## JavaScript (matrix-js-sdk) Quick Snippets

### Initialize
```javascript
const client = sdk.createClient({
  baseUrl: "http://localhost:8008",
  accessToken: "TOKEN",
  userId: "@user:server"
});
await client.startClient();
```

### Send Message
```javascript
await client.sendTextMessage(roomId, "Hello!");
```

### Listen for Events
```javascript
client.on("Room.timeline", (event, room) => {
  if (event.getType() === "m.room.message") {
    console.log(event.getContent().body);
  }
});
```

### Create Room
```javascript
const room = await client.createRoom({
  name: "My Room",
  preset: "private_chat"
});
```

---

## Python (matrix-nio) Quick Snippets

### Initialize
```python
from nio import AsyncClient

client = AsyncClient("http://localhost:8008", "@user:server")
await client.login("password")
```

### Send Message
```python
await client.room_send(
    room_id=room_id,
    message_type="m.room.message",
    content={"msgtype": "m.text", "body": "Hello!"}
)
```

### Sync
```python
sync_response = await client.sync(timeout=30000)
```

---

## Docker Commands

### Start Synapse
```bash
docker run -d --name synapse \
  -p 8008:8008 \
  matrixdotorg/synapse:latest
```

### View Logs
```bash
docker logs -f synapse
```

### Create User
```bash
docker exec -it synapse \
  register_new_matrix_user \
  http://localhost:8008
```

### Stop/Remove
```bash
docker stop synapse
docker rm synapse
```

---

## Debugging Commands

### Test Server
```bash
curl http://localhost:8008/_matrix/client/versions
```

### Test Login
```bash
curl -X POST http://localhost:8008/_matrix/client/v3/login \
  -H "Content-Type: application/json" \
  -d '{"type":"m.login.password","identifier":{"type":"m.id.user","user":"alice"},"password":"pass"}'
```

### Pretty Print JSON
```bash
curl ... | python -m json.tool
# or
curl ... | jq '.'
```

---

## Common Issues & Quick Fixes

| Issue | Fix |
|-------|-----|
| Port in use | `lsof -i :8008` then `kill -9 <PID>` |
| Connection refused | Check if server is running |
| 401 Error | Check access token |
| 403 Error | Check permissions |
| CORS Error | Configure homeserver CORS |
| Rate limit | Add delays between requests |

---

## Development Workflow Checklist

**Setup**
- [ ] Install dependencies
- [ ] Start homeserver
- [ ] Create test user
- [ ] Verify API access

**Development**
- [ ] Implement auth
- [ ] Create/join rooms
- [ ] Send messages
- [ ] Receive messages
- [ ] Handle errors

**Testing**
- [ ] Test happy path
- [ ] Test error cases
- [ ] Test edge cases
- [ ] Test performance

**Polish**
- [ ] Clean up code
- [ ] Add comments
- [ ] Update docs
- [ ] Prepare demo

---

## Essential Links

- Docs: `/docs/INDEX.md`
- Quick Ref: `/docs/QUICK-REFERENCE.md`
- API: `/docs/api-references.md`
- Matrix.org: `https://matrix.org`
- Spec: `https://spec.matrix.org`

---

**For complete documentation, see:** `docs/INDEX.md`

_Last Updated: 2025-10-18_
