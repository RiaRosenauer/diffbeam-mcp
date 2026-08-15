# Security

Do not open a public issue containing a DiffBeam workspace credential, private design, user session, access token, or server vulnerability.

For sensitive reports, use GitHub's private vulnerability reporting for this repository. Include the affected endpoint or document, the minimum reproduction steps, and the impact. Remove all live credentials and personal data from screenshots and request bodies.

The four public MCP tools are anonymous and read-only; they do not grant workspace authority. Workspace operations belong to the Direct Agent Bridge and require a temporary scoped capability issued by the user inside the planner. Credentials belong only in an authenticated JSON request body and must never be sent to the public catalog MCP, stored in URLs, or committed to files.
