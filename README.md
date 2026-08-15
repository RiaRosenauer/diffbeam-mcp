# DiffBeam by Gaussian Beam

DiffBeam is a deterministic Gaussian beam optics service for AI agents and engineering tools. Its anonymous MCP searches optical component catalogs and reports server/catalog revisions. A separate credentialed Direct Agent Bridge analyzes and applies revisioned edits to a user's [Gaussian Beam planner](https://gaussian-beam.com/planner) workspace.

DiffBeam does **not** host or proxy a language model. Bring any compatible AI client.

## Remote MCP server

- Endpoint: `https://catalog-api.gaussian-beam.com/mcp/`
- Release: `2.0.0`
- Registry name: `com.gaussian-beam/diffbeam`
- Human-readable documentation: <https://gaussian-beam.com/mcp/>
- Machine-readable manifest: <https://gaussian-beam.com/.well-known/mcp/server.json>
- Contracts: <https://gaussian-beam.com/mcp/contracts/>

MCP clients connect directly with Streamable HTTP. The public endpoint is anonymous, stateless, and read-only. It has no solver, design-link, or workspace authority.

## No-install Direct Agent Bridge

An internet-capable AI that can send HTTPS POST requests does not need native MCP installation. The planner's **Connect your AI** dialog creates a workspace-specific endpoint, temporary scoped credential, and ready-to-copy prompt. The normal flow is:

1. `get_workspace`
2. make one small planner-native operation such as `add_lens` or `set_wavelength`
3. inspect the returned beam feedback and explain the visible revision
4. refine with the next useful operation; use `dry_run` only for explicit preview-only work

Read the [Direct Agent Bridge guide](https://gaussian-beam.com/mcp/bridge/). Never put a workspace credential in a URL, public page, model configuration, log, or repository.

## Public MCP tools

- `get_diffbeam_state`
- `search_fibers`
- `search_fiber_collimators`
- `search_lenses`

## Credentialed bridge operations

The bridge is not part of the anonymous MCP. It uses the temporary capability
from **Connect your AI** and groups operations into:

- workspace reads, changes, and revision history;
- deterministic solving, beam summaries, waist finding, and point measurement;
- fiber, collimator, and lens catalog searches;
- planner-native source, element, parameter, unit, and beam-target mutations;
- undo and revision restore.

Writes require the current `expected_revision` and create a live planner
revision by default. The public MCP cannot access these operations.

## Worked optical-design guides

- [4F Gaussian beam expander](https://gaussian-beam.com/mcp/guides/4f-beam-expander/)
- [Fiber collimation from mode-field diameter](https://gaussian-beam.com/mcp/guides/fiber-collimation/)
- [Gaussian waist placement](https://gaussian-beam.com/mcp/guides/waist-placement/)
- [Practical focal-length selection](https://gaussian-beam.com/mcp/guides/lens-selection/)
- [MCP examples](https://gaussian-beam.com/mcp/examples/)

The JSON file in `examples/` is a planner-import example for documentation and
bridge workflows. It is not an argument accepted by the anonymous catalog MCP.

## Repository scope

This public repository contains discovery metadata and integration documentation. It deliberately contains no production credentials, private workspace data, telemetry, or deployment configuration. The documents and examples are licensed under Apache-2.0.

Security issues should be reported privately as described in [SECURITY.md](SECURITY.md).
