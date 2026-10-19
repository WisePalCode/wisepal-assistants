# WisePal Free Bill Negotiation

Help users reduce US wireless, internet and TV bills with free WisePal provider negotiations.
Onboarding and exact legal consent happen inside the assistant. No payment method is required;
savings are not guaranteed. Updates go directly to the user's SMS/email.

## Connectors and directories

Choose an installation route below. A downloadable package is separate from approval
in an assistant's official directory. Claude and Muse submissions were confirmed on
October 19, 2026; other directory checkpoints are from October 18. Update these
statuses when approval or publication is confirmed.

| Assistant or directory | Connector and links | Availability |
| --- | --- | --- |
| OpenClaw / ClawHub | [WisePal on ClawHub](https://clawhub.ai/wisepal/wisepal) · [autonomous skill](skills/wisepal/SKILL.md) | Published skill, version 2.0.0. |
| Codex | [OpenAI/Codex remote MCP plugin](plugins/wisepal-openai) · [installation](#connect-with-hosted-mcp) | Public direct install from this repository. |
| Claude Code | [Claude remote MCP plugin](plugins/wisepal-claude) · [installation](#connect-with-hosted-mcp) | Public direct install from this repository. |
| ChatGPT / OpenAI directory | [OpenAI connector package](plugins/wisepal-openai) | Directory version 2.0.2 submitted for review on October 18; public listing not yet confirmed. The repository package remains version 2.0.0. |
| Dots | [Shared OpenAI connector](plugins/wisepal-openai) | Intended to use the OpenAI distribution route; Dots runtime acceptance has not been independently verified. |
| Claude connector directory | [Claude connector package](plugins/wisepal-claude) | Submitted for directory review; approval and public listing have not yet been confirmed. Claude Code direct installation is available separately. |
| Muse | [OAuth OpenAPI draft](https://github.com/WisePalCode/wisepal-assistants/releases/download/v2.0.0/muse-openapi.json) | Submitted for directory review; approval and public listing have not yet been confirmed. |
| Grok / Grok Bot | [Template instructions](https://github.com/WisePalCode/wisepal-assistants/releases/download/v2.0.0/grok-template.md) · [skill package](https://github.com/WisePalCode/wisepal-assistants/releases/download/v2.0.0/wisepal-grok.zip) | Prepared distribution; public bot publication still needs an eligible publisher account and per-user credential-isolation validation. |
| skills.sh / portable skills | [WisePal skill](skills/wisepal/SKILL.md) · [installation](#install-the-autonomous-skill) · [download](https://github.com/WisePalCode/wisepal-assistants/releases/download/v2.0.0/wisepal-skills-sh.zip) | GitHub-based installation is available; a discoverable skills.sh directory listing has not been confirmed. |
| Smithery | [Hosted MCP connection](#connect-with-hosted-mcp) · [Smithery](https://smithery.ai/) | Planned distribution; no published WisePal listing has been verified. |
| Cursor, VS Code / Copilot, Gemini CLI and other assistants | [Connection options](#other-assistants) | Manual integration candidates; individual end-to-end workflows have not been verified. |

The [2.0.0 release](https://github.com/WisePalCode/wisepal-assistants/releases/tag/v2.0.0)
contains the published connector archives and prepared Muse/Grok artifacts.
Pending entries link to their packages or connection details until a public listing exists.

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
