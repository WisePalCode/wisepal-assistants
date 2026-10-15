# WisePal (openai, 2.0.0)

Free US wireless, internet and TV bill negotiation, completed in your assistant.

The hosted MCP is https://my.wisepal.com/mcp (Streamable HTTP). Cloud runtimes use Google OAuth. Only assistant-created accounts can onboard; Google sign-in creates no customer by itself. Explicit confirmation and legal consent are required before provider calls.

This cloud plugin uses runtime OAuth discovery. Select OAuth in the submission portal. No local executor or Python helper is included.

Keep original version 1 clients/private state for existing submissions, or recover using Google with the same email and known submission UUID. Never create a duplicate signup.

[Privacy policy](https://wisepal.com/privacy-policy) · [Terms](https://wisepal.com/terms)
