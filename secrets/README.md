# Secrets

Create these files with your secret values (single line each, `key=value` format).

### Tools & directory

1. `umask 077 && mkdir -p secrets` - create the secrets directory with secure permissions

### Required secrets for this repo

GitHub MCP:

- `github.personal_access_token=<YOUR_GITHUB_PAT>` → `secrets/github_personal_access_token`

Docker Hub MCP:

- `dockerhub.pat_token=<YOUR_DOCKERHUB_PAT>` → `secrets/docker_personal_access_token`

Gateway auth token:

- `MCP_GATEWAY_AUTH_TOKEN=<RANDOM_STRING>` → `secrets/mcp_gateway_auth_token`

### Notes

- Do not commit secrets to git.
- Use per-project tokens and rotate if exposed.
