# WisePal Free Bill Negotiation

Help users reduce US wireless, internet and TV bills with free WisePal provider negotiations.
Signup and exact legal consent are completed inside the assistant. No WisePal login,
preconfigured API key or payment method is required. Savings are not guaranteed.

## Install the skill

```sh
npx skills add WisePalCode/wisepal-assistants --skill wisepal
```

Requires Python 3.10+, outbound HTTPS, and a private persistent filesystem. The CLI
uses only Python's standard library. Read [the skill](skills/wisepal/SKILL.md) before use.
Run it with absolute installed paths and JSON on stdin, as documented in the skill.
Keep `~/.wisepal/agent-onboarding` private and preserve it across updates and restarts.
Do not share a runtime or credential directory between unrelated users.

## Workflow

1. Choose services, collect name/mobile/email, and create a draft with one retained UUID.
2. Collect and validate provider details. Provider login/MFA may require the user's help.
3. Show all validated details and the server's exact terms. Obtain explicit confirmation
   and consent, then approve. Only this step can arrange real provider calls.

Recover receipts using the original UUID and private credential. Never create duplicate
signups to recover lost work. Updates go directly to the user's SMS/email.

## Privacy Policy

[WisePal Privacy Policy](https://wisepal.com/privacy-policy) and
[Terms of Use](https://wisepal.com/terms) apply. Confirmed contact information, US address,
selected providers and account details (including provider-required PINs) are sent to
`https://my.wisepal.com`. The CLI does not request provider passwords, mailbox access or
bill uploads. Submission credentials are saved privately and never returned in CLI output.

This GitHub distribution reports `github-skill` and campaign `assistant-launch`.
Assistant identity remains unknown unless the launcher supplies `WISEPAL_ASSISTANT`.
An installation through the skills CLI still uses this GitHub package's attribution;
the package does not infer which directory or website led the user here.

Package version: 1.0.0. License: MIT-0.

## Local plugins

The plugins run on the user's computer with Python; signup does not require a WisePal login.

Claude Code users can add this marketplace and install the plugin:

```sh
claude plugin marketplace add WisePalCode/wisepal-assistants
claude plugin install wisepal@wisepal
```

Codex users can add the marketplace, then install WisePal from the local plugin directory:

```sh
codex plugin marketplace add WisePalCode/wisepal-assistants
```

Plugin version: 1.0.1. Directory submissions and approvals are separate from this public distribution.
The Grok template and version 1.0.0 downloads remain available in the [release](https://github.com/WisePalCode/wisepal-assistants/releases/tag/v1.0.0).
