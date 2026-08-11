# DiffBeam by Gaussian Beam

DiffBeam is a deterministic Gaussian beam optics service for AI agents and engineering tools. It validates and solves multi-element optical systems, searches local component catalogs, creates immutable design links, and publishes capability-bound live previews to the [Gaussian Beam planner](https://gaussian-beam.com/planner).

DiffBeam does **not** host or proxy a language model. Bring any compatible AI client.

## Remote MCP server

- Endpoint: `https://api.gaussian-beam.com/mcp/`
- Registry name: `com.gaussian-beam/diffbeam`
- Human-readable documentation: <https://gaussian-beam.com/mcp/>
- Machine-readable manifest: <https://gaussian-beam.com/.well-known/mcp/server.json>
- Contracts: <https://gaussian-beam.com/mcp/contracts/>

MCP clients can connect directly with Streamable HTTP. Public tools include validation, deterministic simulation, fiber and lens search, schema discovery, and immutable design-link creation. Workspace tools require a temporary capability created by the user in the planner.

## No-install Direct Agent Bridge

An internet-capable AI that can send HTTPS POST requests does not need native MCP installation. The planner's **Connect your AI** dialog creates a workspace-specific endpoint, temporary scoped credential, and ready-to-copy prompt. The normal flow is:

1. `get_workspace`
2. `preview_workspace_design`
3. explain the calculated preview
4. apply only after user authorization

Read the [Direct Agent Bridge guide](https://gaussian-beam.com/mcp/bridge/). Never put a workspace credential in a URL, public page, model configuration, log, or repository.

## Public MCP tools

- `validate_optical_system`
- `simulate_optical_system`
- `search_fibers`
- `search_fiber_collimators`
- `search_lenses`
- `get_optical_system_schema`
- `create_design_link`

Capability-bound workspace tools:

- `get_workspace`
- `preview_workspace_design`
- `apply_workspace_design`
- `list_workspace_revisions`
- `restore_workspace_revision`

## Worked optical-design guides

- [4F Gaussian beam expander](https://gaussian-beam.com/mcp/guides/4f-beam-expander/)
- [Fiber collimation from mode-field diameter](https://gaussian-beam.com/mcp/guides/fiber-collimation/)
- [Gaussian waist placement](https://gaussian-beam.com/mcp/guides/waist-placement/)
- [Practical focal-length selection](https://gaussian-beam.com/mcp/guides/lens-selection/)
- [MCP examples](https://gaussian-beam.com/mcp/examples/)

## Repository scope

This public repository contains discovery metadata and integration documentation. It deliberately contains no production credentials, private workspace data, telemetry, or deployment configuration. The documents and examples are licensed under Apache-2.0.

Security issues should be reported privately as described in [SECURITY.md](SECURITY.md).
