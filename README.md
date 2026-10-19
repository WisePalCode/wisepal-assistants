# WisePal Free Bill Negotiation

Help users reduce US wireless, internet and TV bills with free WisePal provider negotiations.
Onboarding and exact legal consent happen inside the assistant. No payment method is required;
savings are not guaranteed. Updates go directly to the user's SMS/email.

## Connectors and directories

Choose your assistant below to install WisePal or check its availability.

| Assistant or directory | Connector and links | Availability |
| --- | --- | --- |
| OpenClaw / ClawHub | [WisePal on ClawHub](https://clawhub.ai/wisepal/wisepal) · [autonomous skill](skills/wisepal/SKILL.md) | Available. |
| Codex | [OpenAI/Codex remote MCP plugin](plugins/wisepal-openai) · [installation](#connect-with-hosted-mcp) | Available. |
| Claude Code | [Claude remote MCP plugin](plugins/wisepal-claude) · [installation](#connect-with-hosted-mcp) | Available. |
| ChatGPT / OpenAI directory | [OpenAI connector package](plugins/wisepal-openai) | Pending review / approval. |
| Dots | [Shared OpenAI connector](plugins/wisepal-openai) | Planned via OpenAI; not yet verified. |
| Claude connector directory | [Claude connector package](plugins/wisepal-claude) | Pending review / approval. |
| Muse | [Connector specification](https://github.com/WisePalCode/wisepal-assistants/releases/download/v2.0.0/muse-openapi.json) | Pending review / approval. |
| Grok / Grok Bot | [Template instructions](https://github.com/WisePalCode/wisepal-assistants/releases/download/v2.0.0/grok-template.md) · [skill package](https://github.com/WisePalCode/wisepal-assistants/releases/download/v2.0.0/wisepal-grok.zip) | Template available; public bot not yet available. |
| skills.sh / portable skills | [WisePal skill](skills/wisepal/SKILL.md) · [installation](#install-the-autonomous-skill) · [download](https://github.com/WisePalCode/wisepal-assistants/releases/download/v2.0.0/wisepal-skills-sh.zip) | Install from GitHub. |
| Smithery | [Hosted MCP connection](#connect-with-hosted-mcp) · [Smithery](https://smithery.ai/) | Planned. |
| Cursor, VS Code / Copilot, Gemini CLI and other assistants | [Connection options](#other-assistants) | Manual setup; not yet verified. |

Download connector packages from the
[2.0.0 release](https://github.com/WisePalCode/wisepal-assistants/releases/tag/v2.0.0).

## Connect with hosted MCP

The Streamable HTTP MCP endpoint is `https://my.wisepal.com/mcp`.
Use the assistant runtime's OAuth connection flow and sign in with Google.
Google sign-in creates an authentication identity only. The customer is created when
onboarding begins inside the assistant. Existing ordinary website accounts must continue
on WisePal; only accounts originally created through an assistant can resume here.
The runtime stores OAuth credentials privately. No local MCP server or Python helper is needed.

Claude Code users can install the remote MCP plugin:

```sh
claude plugin marketplace add WisePalCode/wisepal-assistants
claude plugin install wisepal@wisepal
```

Codex users can add this marketplace, then install WisePal from the plugin directory:

```sh
codex plugin marketplace add WisePalCode/wisepal-assistants
```

These public packages are direct-install distributions. Directory review and approval
are separate. See the [OpenAI plugin](plugins/wisepal-openai) or
[Claude plugin](plugins/wisepal-claude) for package details.

## Install the autonomous skill

```sh
npx skills add WisePalCode/wisepal-assistants --skill wisepal
```

Requires Python 3.10+, outbound HTTPS, and private persistent storage. The standard-library
CLI obtains a server-issued token autonomously and stores it privately; no website login
or preconfigured API key is needed. Read [the skill](skills/wisepal/SKILL.md) before use.
Run commands using absolute installed paths and JSON on stdin. Never expose tokens in
chat, shared logs, tool arguments, or model-visible credential-hook results. Never share
credential storage between unrelated customers. This GitHub package reports `github-skill`
and campaign `assistant-launch`; assistant identity is supplied only by a knowledgeable launcher.

## Other assistants

Assistants with remote Streamable HTTP MCP and runtime-managed OAuth can connect to
[WisePal's hosted MCP](https://my.wisepal.com/mcp). Use the host assistant's native MCP
configuration and Google authorization flow; there is no WisePal local MCP server to run.

Assistants with a Python executor and private persistent credential storage can use
[the autonomous skill](skills/wisepal/SKILL.md). Each unrelated user needs isolated
credentials. Support for MCP or skills alone does not establish that a specific assistant
has completed WisePal's onboarding and consent workflow.

## Workflow and recovery

1. Choose services, collect name/mobile/email, and begin with one retained UUID.
2. Collect and validate provider details. Provider login/MFA may require user assistance.
3. Display every validated detail and the exact server-provided legal terms. Obtain explicit
   confirmation and consent before approval can arrange real provider calls.

Preserve original version 1 clients and their private state for existing submissions.
Version 2 uses a separate state directory. Restore a lost credential or reconnect using
Google with the same email and known submission UUID; never create a duplicate signup
to recover an intake. A missing, expired, or revoked credential must not trigger replacement
onboarding. Old [1.0.0](https://github.com/WisePalCode/wisepal-assistants/releases/tag/v1.0.0)
and [1.0.1](https://github.com/WisePalCode/wisepal-assistants/releases/tag/v1.0.1)
release assets remain available.

## Privacy

[WisePal Privacy Policy](https://wisepal.com/privacy-policy) and
[Terms of Use](https://wisepal.com/terms) apply. Confirmed contact details, US address,
selected providers and account details, including provider-required PINs, are sent to
`https://my.wisepal.com`. Provider passwords, mailbox access and bill uploads are not
accepted by these onboarding tools. Credentials remain in the runtime's private storage.

Version 2.0.0. License: MIT-0.
