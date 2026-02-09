# docker-ai-mcp

A self-contained Docker MCP Gateway with repo-managed configuration, secure secrets wiring, and controlled filesystem access, designed to run consistently across machines.

## Quick start (Docker Compose)

> [!NOTE]
>
> You need Docker Engine and Docker Compose v2.20+ installed before running this project.
>
> Docker Desktop MCP Toolkit:
> - Compose-only: toggle not required
> - Using `docker mcp ...` CLI: toggle required

1. Clone this repository and enter the project directory.
2. Copy `env-example` to `.env` and update values as needed.
3. Populate `./secrets/*` with your secrets (see `secrets/README.md`).
4. Update `config/config.yaml` to add allowed paths for the filesystem MCP server.
5. `docker compose up -d` - to start the gateway

### Default MCP servers

These are controlled by `MCP_SERVERS` in `.env` (comma-separated):

| Server ID         | Secrets required                       | Notes                                             |
| ----------------- | -------------------------------------- | ------------------------------------------------- |
| `github-official` | `secrets/github_personal_access_token` | GitHub API access                                 |
| `filesystem`      | None                                   | Requires paths in `config/config.yaml` allow-list |
| `fetch`           | None                                   | Public HTTP fetcher                               |
| `dockerhub`       | `secrets/docker_personal_access_token` | Docker Hub API access                             |
| `context7`        | None                                   | Documentation search (Context7)                   |

Find all available server IDs by running `docker.exe mcp catalog ls --format json`

## Streamable gateway client config

Use this when connecting from a local or LAN client (VS Code, Claude, etc.) to the gateway running on this host.

### Client config for Visual Studio Code:

```json
{
  "mcpServers": {
    "docker-mcp-gateway": {
      "type": "streamable",
      "url": "http://<SERVER IP>:8811/mcp"
    }
  }
}
```
