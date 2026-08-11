# Security

Do not open a public issue containing a DiffBeam workspace credential, private design, user session, access token, or server vulnerability.

For sensitive reports, use GitHub's private vulnerability reporting for this repository. Include the affected endpoint or document, the minimum reproduction steps, and the impact. Remove all live credentials and personal data from screenshots and request bodies.

The public MCP tools do not grant workspace authority. Workspace operations require a temporary scoped capability issued by the user inside the planner. Credentials belong only in an authenticated request body and must never be stored in URLs or committed files.
