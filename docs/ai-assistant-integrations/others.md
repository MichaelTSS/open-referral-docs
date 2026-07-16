# Others (any MCP client)

Open Referral exposes a standard remote **MCP (Model Context Protocol)** server, so it
works with any client that supports custom MCP connectors — not only the assistants
documented here.

* **Server URL:** `https://mcp.openreferral.io`
* **Transport:** Streamable HTTP
* **Authentication:** OAuth 2.1 (Dynamic Client Registration, PKCE) or a personal Bearer token
* **Capabilities:** 7 read-only tools

If your assistant follows the MCP specification, add Open Referral as a custom connector
using the URL above and authenticate with your Open Referral account.
