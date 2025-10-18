# LuxChat Hackathon - Quick Reference

A condensed reference guide for quick lookups during the hackathon.

## 🔗 Essential Links

| Resource | URL |
|----------|-----|
| Matrix.org | https://matrix.org/ |
| Matrix Spec | https://spec.matrix.org/ |
| Client-Server API | https://spec.matrix.org/latest/client-server-api/ |
| Matrix SDKs | https://matrix.org/sdks/ |
| Element Web Client | https://app.element.io/ |

## 📚 Documentation Quick Links

- [Getting Started](./getting-started.md) - Start here
- [Matrix Protocol](./matrix-protocol.md) - Protocol overview
- [Development Setup](./development-setup.md) - Environment setup
- [API References](./api-references.md) - API details
- [Tools & Utilities](./tools-and-utilities.md) - Development tools

## 🚀 Quick Start Commands

### Set up local Matrix homeserver (Docker)

```bash
# Start Synapse
docker run -d --name synapse \
  -p 8008:8008 \
  -e SYNAPSE_SERVER_NAME=localhost \
  -e SYNAPSE_REPORT_STATS=no \
  matrixdotorg/synapse:latest

# Create a test user
docker exec -it synapse register_new_matrix_user \
  -c /data/homeserver.yaml http://localhost:8008
```

### Basic Matrix API Calls

#### Login
```bash
curl -X POST "http://localhost:8008/_matrix/client/v3/login" \
  -H "Content-Type: application/json" \
  -d '{
    "type": "m.login.password",
    "identifier": {"type": "m.id.user", "user": "alice"},
    "password": "password"
  }'
```

#### Create Room
```bash
curl -X POST "http://localhost:8008/_matrix/client/v3/createRoom" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"name": "Test Room"}'
```

#### Send Message
```bash
curl -X PUT "http://localhost:8008/_matrix/client/v3/rooms/ROOM_ID/send/m.room.message/TXN_ID" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"msgtype": "m.text", "body": "Hello!"}'
```

#### Sync
```bash
curl "http://localhost:8008/_matrix/client/v3/sync" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

## 💻 Common Code Patterns

### JavaScript/TypeScript (matrix-js-sdk)

#### Initialize Client
```javascript
const sdk = require("matrix-js-sdk");

const client = sdk.createClient({
  baseUrl: "http://localhost:8008",
  accessToken: "YOUR_TOKEN",
  userId: "@alice:localhost"
});

await client.startClient({ initialSyncLimit: 10 });
```

#### Send Message
```javascript
await client.sendTextMessage(roomId, "Hello, World!");
```

#### Listen for Messages
```javascript
client.on("Room.timeline", (event, room, toStartOfTimeline) => {
  if (event.getType() === "m.room.message") {
    console.log(event.getContent().body);
  }
});
```

### Python (matrix-nio)

#### Initialize Client
```python
from nio import AsyncClient

client = AsyncClient("http://localhost:8008", "@alice:localhost")
await client.login("password")
```

#### Send Message
```python
from nio import RoomMessageText

await client.room_send(
    room_id=room_id,
    message_type="m.room.message",
    content={"msgtype": "m.text", "body": "Hello!"}
)
```

## 🔑 Key Concepts

### Matrix Identifiers

| Type | Format | Example |
|------|--------|---------|
| User ID | `@user:server` | `@alice:matrix.org` |
| Room ID | `!room:server` | `!abc123:matrix.org` |
| Room Alias | `#alias:server` | `#general:matrix.org` |
| Event ID | `$event:server` | `$xyz789:matrix.org` |

### Event Types

| Type | Description |
|------|-------------|
| `m.room.message` | Regular message |
| `m.room.encrypted` | Encrypted message |
| `m.room.member` | Membership change |
| `m.room.name` | Room name change |
| `m.room.topic` | Room topic change |
| `m.typing` | Typing notification |
| `m.receipt` | Read receipt |

### Message Types

| msgtype | Use Case |
|---------|----------|
| `m.text` | Plain text message |
| `m.emote` | Emote action |
| `m.notice` | Bot/system notice |
| `m.image` | Image message |
| `m.file` | File attachment |
| `m.video` | Video message |
| `m.audio` | Audio message |

## 🛠️ Debugging Tips

### Check Homeserver Status
```bash
curl http://localhost:8008/_matrix/client/versions
```

### View Docker Logs
```bash
docker logs synapse
docker logs -f synapse  # Follow logs
```

### Common Issues

| Issue | Solution |
|-------|----------|
| Connection refused | Check homeserver is running |
| 401 Unauthorized | Verify access token |
| 403 Forbidden | Check user permissions |
| CORS errors | Configure CORS in homeserver |
| Rate limiting | Add delays between requests |

## 📊 HTTP Status Codes

| Code | Meaning |
|------|---------|
| 200 | Success |
| 400 | Bad request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not found |
| 429 | Rate limited |
| 500 | Server error |

## 🎯 Hackathon Checklist

### Setup Phase
- [ ] Environment configured
- [ ] Matrix homeserver running
- [ ] Test account created
- [ ] SDK installed and tested
- [ ] Documentation reviewed

### Development Phase
- [ ] Authentication working
- [ ] Room creation working
- [ ] Message sending working
- [ ] Message receiving working
- [ ] Error handling implemented

### Polish Phase
- [ ] Code cleaned up
- [ ] Documentation updated
- [ ] Testing completed
- [ ] Demo prepared

## 📱 Testing Tools

### Command Line
```bash
# Test API endpoint
curl -X GET "http://localhost:8008/_matrix/client/versions"

# Pretty print JSON
curl ... | python -m json.tool
curl ... | jq '.'
```

### Browser
- Open browser DevTools (F12)
- Use Network tab to inspect API calls
- Use Console for debugging

## 🔐 Security Notes

- Never commit access tokens
- Use environment variables for secrets
- Test with local homeserver first
- Verify device keys in E2EE
- Clear sensitive data from logs

## 📞 Getting Help

1. Check [Getting Started guide](./getting-started.md)
2. Review [API References](./api-references.md)
3. Search [Matrix documentation](https://matrix.org/docs/)
4. Ask in team chat
5. Check [External Resources](./resources/external-links.md)

## 🎨 UI/UX Considerations

- Show loading states
- Handle errors gracefully
- Display typing indicators
- Show read receipts
- Implement message history
- Support media previews
- Add user presence indicators

## ⚡ Performance Tips

- Implement pagination
- Use lazy loading
- Cache room state
- Optimize image sizes
- Debounce user input
- Use virtual scrolling
- Implement connection retry logic

## 📝 Documentation Templates

### Code Comments
```javascript
/**
 * Sends a message to a Matrix room
 * @param {string} roomId - The room ID
 * @param {string} message - The message text
 * @returns {Promise<string>} The event ID
 */
async function sendMessage(roomId, message) {
  // Implementation
}
```

### Error Handling
```javascript
try {
  await client.sendMessage(roomId, message);
} catch (error) {
  if (error.httpStatus === 429) {
    // Rate limited - retry after delay
  } else if (error.httpStatus === 403) {
    // Forbidden - check permissions
  } else {
    // Handle other errors
  }
}
```

## 🚦 Development Workflow

1. **Plan**: Define features and requirements
2. **Setup**: Configure environment
3. **Develop**: Implement features iteratively
4. **Test**: Verify functionality
5. **Debug**: Fix issues
6. **Polish**: Improve UX and code quality
7. **Document**: Update documentation
8. **Demo**: Prepare presentation

---

**Last Updated**: 2025-10-18  
**For Full Documentation**: See [docs/INDEX.md](./INDEX.md)
