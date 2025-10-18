---
layout: default
title: Development Setup
---

# Development Setup

## Local Matrix Homeserver

### Using Synapse with Docker

```bash
docker run -d --name synapse \
  -p 8008:8008 \
  -e SYNAPSE_SERVER_NAME=localhost \
  matrixdotorg/synapse:latest
```

Create a user:
```bash
docker exec -it synapse register_new_matrix_user \
  http://localhost:8008
```

## Project Setup

[TODO]

## Resources

- [Synapse Documentation](https://matrix-org.github.io/synapse/latest/)
- [Matrix Client-Server API](https://spec.matrix.org/latest/client-server-api/)
