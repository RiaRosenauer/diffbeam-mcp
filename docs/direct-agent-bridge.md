# Direct Agent Bridge

The Direct Agent Bridge lets an internet-capable AI agent analyze and apply planner-native, revisioned edits to an existing DiffBeam workspace without installing native MCP.

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
{"operation":"read_beam_summary","workspace_credential":"<temporary credential>","detail":"summary"}
```

```json
{"operation":"add_lens","workspace_credential":"<temporary credential>","expected_revision":3,"focal_length_value":50,"focal_length_unit":"mm","distance_value":50,"distance_unit":"mm"}
```

Planner-native mutations create a live revision by default. Applying requires the appropriate scope, the exact current `expected_revision`, and user authorization; a stale revision returns a conflict. Set `dry_run` only when the user explicitly asks for preview-only exploration.

The bridge also supports source initialization, wavelength and unit changes, Galilean and Keplerian expanders, apertures, ABCD matrices, element ordering and locking, parameter formulas and fixed/free state, beam targets, catalog references, workspace changes, solving, waist finding, point measurements, catalog search, undo, and revision restore. Full documentation is maintained at <https://gaussian-beam.com/mcp/bridge/>.

The anonymous public MCP is a separate four-tool surface at <https://catalog-api.gaussian-beam.com/mcp/>. It can report DiffBeam revisions and search fibers, fiber collimators, and lenses; it cannot read or edit a workspace. Never send a workspace credential to that endpoint.
