# Direct Agent Bridge

The Direct Agent Bridge lets an internet-capable AI agent publish calculated previews to an existing DiffBeam workspace without installing native MCP.

The user first opens the [DiffBeam planner](https://gaussian-beam.com/planner), clicks **Connect your AI**, and copies the generated prompt. That prompt contains a workspace-specific endpoint and temporary credential. This repository never contains a live credential.

Endpoint template:

```text
https://api.gaussian-beam.com/api/agent/workspaces/{public_workspace_id}
```

Commands are JSON POST requests with `Content-Type: application/json`:

```json
{"operation":"get_workspace","workspace_credential":"<temporary credential>"}
```

```json
{"operation":"preview_workspace_design","workspace_credential":"<temporary credential>","spec":{"wavelength":{"value":689,"unit":"nm","fixed":true},"optical_chain":[]}}
```

```json
{"operation":"apply_workspace_design","workspace_credential":"<temporary credential>","expected_revision":3,"spec":{"wavelength":{"value":689,"unit":"nm","fixed":true},"optical_chain":[]}}
```

Preview is the default. Applying requires the appropriate scope, an exact expected revision, and user authorization. Full documentation is maintained at <https://gaussian-beam.com/mcp/bridge/>.
