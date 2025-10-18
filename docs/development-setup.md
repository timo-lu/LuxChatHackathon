# Development Setup

## Prerequisites

Before setting up the development environment, ensure you have:

### Required Software

- [ ] **Git**: Version control system
  - Download: [https://git-scm.com/](https://git-scm.com/)
  - Verify: `git --version`

- [ ] **Node.js**: JavaScript runtime (if applicable)
  - Download: [https://nodejs.org/](https://nodejs.org/) (LTS version recommended)
  - Verify: `node --version` and `npm --version`

- [ ] **Python**: (if backend is Python-based)
  - Download: [https://python.org/](https://python.org/)
  - Verify: `python --version` or `python3 --version`

- [ ] **Docker**: For running Matrix homeserver locally
  - Download: [https://www.docker.com/](https://www.docker.com/)
  - Verify: `docker --version`

### Recommended Tools

- **IDE/Editor**: VS Code, WebStorm, or your preferred editor
- **Git Client**: GitHub Desktop, GitKraken, or command line
- **API Testing**: Postman, Insomnia, or curl
- **Database Client**: DBeaver, pgAdmin (if using PostgreSQL)

## Setting Up LuxChat

### 1. Clone the Repository

```bash
git clone https://github.com/[organization]/luxchat.git
cd luxchat
```

### 2. Install Dependencies

#### For Node.js projects:
```bash
npm install
# or
yarn install
# or
pnpm install
```

#### For Python projects:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Environment Configuration

Create a `.env` file in the project root:

```env
# Matrix Homeserver Configuration
MATRIX_HOMESERVER_URL=http://localhost:8008
MATRIX_ACCESS_TOKEN=your_access_token_here

# Application Configuration
APP_ENV=development
APP_PORT=3000
APP_HOST=localhost

# Database Configuration (if applicable)
DATABASE_URL=postgresql://user:password@localhost:5432/luxchat

# Encryption (if applicable)
ENCRYPTION_KEY=your_encryption_key_here

# Logging
LOG_LEVEL=debug
```

### 4. Database Setup (if applicable)

```bash
# Create database
createdb luxchat

# Run migrations
npm run migrate
# or
python manage.py migrate
```

## Setting Up a Local Matrix Homeserver

### Option 1: Using Synapse with Docker

Create a `docker-compose.yml` file:

```yaml
version: '3'

services:
  synapse:
    image: matrixdotorg/synapse:latest
    container_name: synapse
    ports:
      - "8008:8008"
    environment:
      - SYNAPSE_SERVER_NAME=localhost
      - SYNAPSE_REPORT_STATS=no
    volumes:
      - ./synapse-data:/data
```

Start the homeserver:

```bash
# Generate configuration
docker run -it --rm \
  -v ${PWD}/synapse-data:/data \
  -e SYNAPSE_SERVER_NAME=localhost \
  -e SYNAPSE_REPORT_STATS=no \
  matrixdotorg/synapse:latest generate

# Start Synapse
docker-compose up -d

# Create a user
docker exec -it synapse register_new_matrix_user \
  -c /data/homeserver.yaml http://localhost:8008
```

### Option 2: Using Dendrite (Lightweight Alternative)

```bash
docker run -d --name dendrite \
  -p 8008:8008 \
  matrixdotorg/dendrite-monolith:latest
```

### Verify Homeserver

```bash
curl http://localhost:8008/_matrix/client/versions
```

You should see a JSON response with supported Matrix API versions.

## Running LuxChat

### Development Mode

#### Frontend (if separate):
```bash
npm run dev
# or
yarn dev
```

Access at: `http://localhost:3000`

#### Backend (if applicable):
```bash
npm run server
# or
python manage.py runserver
```

### Running Tests

```bash
# Unit tests
npm test
# or
pytest

# E2E tests
npm run test:e2e

# Watch mode
npm test -- --watch
```

### Building for Production

```bash
npm run build
# or
yarn build
```

## IDE Configuration

### VS Code

Install recommended extensions:

```json
{
  "recommendations": [
    "dbaeumer.vscode-eslint",
    "esbenp.prettier-vscode",
    "ms-vscode.vscode-typescript-next",
    "bradlc.vscode-tailwindcss"
  ]
}
```

Create `.vscode/settings.json`:

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

### WebStorm

1. Enable ESLint: `Settings > Languages & Frameworks > JavaScript > Code Quality Tools > ESLint`
2. Enable Prettier: `Settings > Languages & Frameworks > JavaScript > Prettier`
3. Set up run configurations for npm scripts

## Debugging

### Browser DevTools

1. Open browser developer tools (F12)
2. Use Console for logging
3. Use Network tab to monitor API calls
4. Use Application tab to inspect local storage

### VS Code Debugging

Create `.vscode/launch.json`:

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "chrome",
      "request": "launch",
      "name": "Launch Chrome",
      "url": "http://localhost:3000",
      "webRoot": "${workspaceFolder}/src"
    },
    {
      "type": "node",
      "request": "launch",
      "name": "Launch Server",
      "program": "${workspaceFolder}/server/index.js"
    }
  ]
}
```

### Matrix SDK Debugging

Enable debug logging:

```javascript
// For matrix-js-sdk
const sdk = require("matrix-js-sdk");
sdk.logger.setLevel("debug");
```

## Common Issues & Solutions

### Port Already in Use

```bash
# Find process using port 3000
lsof -i :3000
# or on Windows
netstat -ano | findstr :3000

# Kill the process
kill -9 <PID>
```

### CORS Issues

If you encounter CORS errors when connecting to the homeserver, configure CORS in your homeserver config:

```yaml
# For Synapse: homeserver.yaml
listeners:
  - port: 8008
    bind_addresses: ['0.0.0.0']
    type: http
    tls: false
    x_forwarded: true
    resources:
      - names: [client, federation]
        compress: false
```

Add CORS headers:

```yaml
web_client_location: http://localhost:3000
```

### Connection Refused

Ensure your Matrix homeserver is running:

```bash
docker ps
# Should show synapse container

# Check logs
docker logs synapse
```

### Module Not Found

Clear cache and reinstall:

```bash
rm -rf node_modules package-lock.json
npm install
```

## Next Steps

- [ ] Review [Getting Started Guide](./getting-started.md)
- [ ] Understand [Matrix Protocol](./matrix-protocol.md)
- [ ] Explore [LuxChat Architecture](./luxchat-architecture.md)
- [ ] Check [API References](./api-references.md)
- [ ] Try [Tools & Utilities](./tools-and-utilities.md)

## Additional Resources

- [Matrix Synapse Documentation](https://matrix-org.github.io/synapse/latest/)
- [Matrix Client-Server API](https://spec.matrix.org/latest/client-server-api/)
- [Docker Documentation](https://docs.docker.com/)
- [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)

## Support

If you encounter issues:

1. Check the [troubleshooting section](#common-issues--solutions)
2. Search existing issues in the repository
3. Ask in the team chat channel
4. Create a new issue with detailed information
