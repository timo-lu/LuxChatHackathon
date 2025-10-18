# Tools & Utilities

## Matrix Development Tools

### Matrix SDK Libraries

#### JavaScript/TypeScript
- **matrix-js-sdk**: Official Matrix SDK for JavaScript
  - Repository: [https://github.com/matrix-org/matrix-js-sdk](https://github.com/matrix-org/matrix-js-sdk)
  - npm: `npm install matrix-js-sdk`
  - Documentation: [https://matrix-org.github.io/matrix-js-sdk/](https://matrix-org.github.io/matrix-js-sdk/)

#### Rust
- **matrix-rust-sdk**: High-performance SDK for Rust
  - Repository: [https://github.com/matrix-org/matrix-rust-sdk](https://github.com/matrix-org/matrix-rust-sdk)
  - Cargo: `cargo add matrix-sdk`
  - Documentation: [https://docs.rs/matrix-sdk/](https://docs.rs/matrix-sdk/)

#### Python
- **matrix-nio**: Async Python Matrix client library
  - Repository: [https://github.com/poljar/matrix-nio](https://github.com/poljar/matrix-nio)
  - pip: `pip install matrix-nio`
  - Documentation: [https://matrix-nio.readthedocs.io/](https://matrix-nio.readthedocs.io/)

#### Mobile SDKs
- **matrix-android-sdk2**: Android SDK (Kotlin)
  - Repository: [https://github.com/matrix-org/matrix-android-sdk2](https://github.com/matrix-org/matrix-android-sdk2)
  
- **matrix-ios-sdk**: iOS SDK (Swift)
  - Repository: [https://github.com/matrix-org/matrix-ios-sdk](https://github.com/matrix-org/matrix-ios-sdk)

### Matrix Homeserver Software

#### Synapse (Python)
- **Description**: Reference Matrix homeserver implementation
- Repository: [https://github.com/matrix-org/synapse](https://github.com/matrix-org/synapse)
- Documentation: [https://matrix-org.github.io/synapse/](https://matrix-org.github.io/synapse/)
- Docker: `docker pull matrixdotorg/synapse`

#### Dendrite (Go)
- **Description**: Next-generation Matrix homeserver
- Repository: [https://github.com/matrix-org/dendrite](https://github.com/matrix-org/dendrite)
- Documentation: [https://matrix-org.github.io/dendrite/](https://matrix-org.github.io/dendrite/)
- Docker: `docker pull matrixdotorg/dendrite-monolith`

#### Conduit (Rust)
- **Description**: Lightweight Matrix homeserver
- Repository: [https://gitlab.com/famedly/conduit](https://gitlab.com/famedly/conduit)
- Docker: `docker pull matrixconduit/matrix-conduit`

### Matrix Clients (for Testing)

#### Element Web
- **Description**: Official Matrix web client
- URL: [https://app.element.io/](https://app.element.io/)
- Repository: [https://github.com/vector-im/element-web](https://github.com/vector-im/element-web)

#### Element Desktop
- Downloads: [https://element.io/download](https://element.io/download)

#### Element Mobile
- Android: [Google Play Store](https://play.google.com/store/apps/details?id=im.vector.app)
- iOS: [App Store](https://apps.apple.com/app/element-messenger/id1083446067)

## Development Tools

### API Testing

#### Postman
- **Description**: API development and testing tool
- Download: [https://www.postman.com/downloads/](https://www.postman.com/downloads/)
- Matrix API Collection: Import from Matrix.org

#### Insomnia
- **Description**: REST API client
- Download: [https://insomnia.rest/download](https://insomnia.rest/download)

#### curl
- Command-line tool for API testing
- Example:
  ```bash
  curl -X GET "https://matrix.org/_matrix/client/versions"
  ```

### Database Tools

#### DBeaver
- **Description**: Universal database tool
- Download: [https://dbeaver.io/download/](https://dbeaver.io/download/)
- Supports: PostgreSQL, SQLite, MySQL, etc.

#### pgAdmin
- **Description**: PostgreSQL management tool
- Download: [https://www.pgadmin.org/download/](https://www.pgadmin.org/download/)

### Docker Tools

#### Docker Desktop
- Download: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
- Includes Docker and Docker Compose

#### Portainer
- **Description**: Docker container management UI
- Installation:
  ```bash
  docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer-ce
  ```

### Code Editors & IDEs

#### Visual Studio Code
- Download: [https://code.visualstudio.com/](https://code.visualstudio.com/)
- Recommended Extensions:
  - ESLint
  - Prettier
  - GitLens
  - REST Client
  - Docker

#### WebStorm
- Download: [https://www.jetbrains.com/webstorm/](https://www.jetbrains.com/webstorm/)
- Free for students and open source projects

#### IntelliJ IDEA
- Download: [https://www.jetbrains.com/idea/](https://www.jetbrains.com/idea/)

### Git Tools

#### GitHub Desktop
- Download: [https://desktop.github.com/](https://desktop.github.com/)

#### GitKraken
- Download: [https://www.gitkraken.com/](https://www.gitkraken.com/)

#### SourceTree
- Download: [https://www.sourcetreeapp.com/](https://www.sourcetreeapp.com/)

## Debugging & Monitoring

### Browser DevTools
- **Chrome DevTools**: Built into Chrome (F12)
- **Firefox Developer Tools**: Built into Firefox (F12)
- **React DevTools**: [Chrome Extension](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)

### Network Debugging

#### Wireshark
- **Description**: Network protocol analyzer
- Download: [https://www.wireshark.org/](https://www.wireshark.org/)

#### Charles Proxy
- **Description**: HTTP debugging proxy
- Download: [https://www.charlesproxy.com/](https://www.charlesproxy.com/)

#### Fiddler
- **Description**: Web debugging proxy
- Download: [https://www.telerik.com/fiddler](https://www.telerik.com/fiddler)

### Log Management

#### Logstash
- Part of the ELK stack
- Website: [https://www.elastic.co/logstash](https://www.elastic.co/logstash)

#### Sentry
- **Description**: Error tracking and monitoring
- Website: [https://sentry.io/](https://sentry.io/)

## Testing Tools

### Unit Testing

#### Jest
- **Description**: JavaScript testing framework
- Website: [https://jestjs.io/](https://jestjs.io/)
- Installation: `npm install --save-dev jest`

#### Pytest
- **Description**: Python testing framework
- Website: [https://pytest.org/](https://pytest.org/)
- Installation: `pip install pytest`

#### Mocha
- **Description**: JavaScript test framework
- Website: [https://mochajs.org/](https://mochajs.org/)
- Installation: `npm install --save-dev mocha`

### E2E Testing

#### Playwright
- **Description**: End-to-end testing framework
- Website: [https://playwright.dev/](https://playwright.dev/)
- Installation: `npm install --save-dev @playwright/test`

#### Cypress
- **Description**: E2E testing for web applications
- Website: [https://www.cypress.io/](https://www.cypress.io/)
- Installation: `npm install --save-dev cypress`

#### Selenium
- **Description**: Browser automation
- Website: [https://www.selenium.dev/](https://www.selenium.dev/)

### Load Testing

#### k6
- **Description**: Load testing tool
- Website: [https://k6.io/](https://k6.io/)
- Installation: [https://k6.io/docs/get-started/installation/](https://k6.io/docs/get-started/installation/)

#### Apache JMeter
- **Description**: Load testing application
- Website: [https://jmeter.apache.org/](https://jmeter.apache.org/)

## Utility Libraries

### Cryptography

#### Olm/Megolm
- **Description**: Cryptographic ratchets used by Matrix
- Repository: [https://gitlab.matrix.org/matrix-org/olm](https://gitlab.matrix.org/matrix-org/olm)

#### libsodium
- **Description**: Modern cryptography library
- Website: [https://libsodium.gitbook.io/](https://libsodium.gitbook.io/)

### UI Components

#### Material-UI (React)
- Website: [https://mui.com/](https://mui.com/)
- Installation: `npm install @mui/material @emotion/react @emotion/styled`

#### Ant Design (React)
- Website: [https://ant.design/](https://ant.design/)
- Installation: `npm install antd`

#### Vuetify (Vue)
- Website: [https://vuetifyjs.com/](https://vuetifyjs.com/)
- Installation: `npm install vuetify`

### State Management

#### Redux (React)
- Website: [https://redux.js.org/](https://redux.js.org/)
- Installation: `npm install @reduxjs/toolkit react-redux`

#### Zustand (React)
- Website: [https://github.com/pmndrs/zustand](https://github.com/pmndrs/zustand)
- Installation: `npm install zustand`

#### Pinia (Vue)
- Website: [https://pinia.vuejs.org/](https://pinia.vuejs.org/)
- Installation: `npm install pinia`

## Documentation Tools

### Markdown Editors

#### Typora
- Download: [https://typora.io/](https://typora.io/)

#### Mark Text
- Download: [https://marktext.app/](https://marktext.app/)

#### VS Code with Markdown Preview
- Built-in markdown preview
- Extensions: Markdown All in One, Markdown Preview Enhanced

### Diagram Tools

#### Mermaid
- **Description**: Markdown-based diagrams
- Website: [https://mermaid.js.org/](https://mermaid.js.org/)
- Live Editor: [https://mermaid.live/](https://mermaid.live/)

#### Draw.io
- **Description**: Diagramming tool
- Website: [https://draw.io/](https://draw.io/)
- VS Code Extension: Draw.io Integration

#### Excalidraw
- **Description**: Virtual whiteboard
- Website: [https://excalidraw.com/](https://excalidraw.com/)

#### PlantUML
- **Description**: Text-based UML diagrams
- Website: [https://plantuml.com/](https://plantuml.com/)

### API Documentation

#### Swagger/OpenAPI
- Website: [https://swagger.io/](https://swagger.io/)

#### Docusaurus
- Website: [https://docusaurus.io/](https://docusaurus.io/)
- Installation: `npx create-docusaurus@latest`

## Matrix-Specific Utilities

### Matrix CLI Tools

#### matrixcli
- Python-based Matrix CLI client
- Installation: `pip install matrix-client`

### Room Directory Browsers

#### Matrix Public Rooms
- Browse public rooms: [https://view.matrix.org/](https://view.matrix.org/)

### Matrix Bots

#### matrix-bot-sdk
- Repository: [https://github.com/turt2live/matrix-bot-sdk](https://github.com/turt2live/matrix-bot-sdk)
- Installation: `npm install matrix-bot-sdk`

#### maubot
- Python bot framework
- Repository: [https://github.com/maubot/maubot](https://github.com/maubot/maubot)

## Performance Tools

### Lighthouse
- **Description**: Web performance auditing
- Built into Chrome DevTools
- CLI: `npm install -g lighthouse`

### Webpack Bundle Analyzer
- Installation: `npm install --save-dev webpack-bundle-analyzer`

### Chrome Performance Monitor
- Built into Chrome DevTools

## Code Quality Tools

### Linters

#### ESLint (JavaScript)
- Installation: `npm install --save-dev eslint`
- Config: `.eslintrc.js`

#### Pylint (Python)
- Installation: `pip install pylint`

#### Clippy (Rust)
- Built into Rust toolchain: `rustup component add clippy`

### Formatters

#### Prettier
- Installation: `npm install --save-dev prettier`
- Config: `.prettierrc`

#### Black (Python)
- Installation: `pip install black`

### Type Checking

#### TypeScript
- Installation: `npm install --save-dev typescript`

#### mypy (Python)
- Installation: `pip install mypy`

## Collaboration Tools

### Communication
- **Discord**: [https://discord.com/](https://discord.com/)
- **Slack**: [https://slack.com/](https://slack.com/)
- **Matrix**: Use Element or LuxChat!

### Project Management
- **GitHub Projects**: Built into GitHub
- **Trello**: [https://trello.com/](https://trello.com/)
- **Jira**: [https://www.atlassian.com/software/jira](https://www.atlassian.com/software/jira)

## Quick Reference Commands

### npm Scripts
```bash
npm install              # Install dependencies
npm run dev             # Start development server
npm run build           # Build for production
npm test                # Run tests
npm run lint            # Run linter
npm run format          # Format code
```

### Docker Commands
```bash
docker ps               # List running containers
docker logs <container> # View container logs
docker exec -it <container> bash  # Enter container shell
docker-compose up -d    # Start services in background
docker-compose down     # Stop services
```

### Git Commands
```bash
git status              # Check status
git add .               # Stage all changes
git commit -m "msg"     # Commit changes
git push                # Push to remote
git pull                # Pull from remote
git branch              # List branches
git checkout -b <name>  # Create and switch to new branch
```

## Next Steps

- Review [API References](./api-references.md) for Matrix API details
- Check [Development Setup](./development-setup.md) for environment setup
- Explore [Matrix Protocol](./matrix-protocol.md) for protocol understanding

## Contributing

If you find a useful tool not listed here, please add it! Keep the format consistent and include:
- Tool name and description
- Website/repository link
- Installation instructions
- Brief explanation of when to use it
