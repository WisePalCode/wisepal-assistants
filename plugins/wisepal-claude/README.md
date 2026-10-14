# WisePal free bill negotiation (claude, 1.0.1)

Free US wireless, internet and TV bill negotiation, completed in your assistant. No WisePal login, preconfigured API key or payment method is required.

Requires Python 3.10+ and an assistant runtime with a private, persistent filesystem and outbound HTTPS. The assistant runs `skills/wisepal/scripts/wisepal.py`; the CLI needs no third-party dependencies. Read `skills/wisepal/SKILL.md` before onboarding.

Install this plugin/skill in a private per-user runtime. Keep `~/.wisepal/agent-onboarding` outside the package and preserve it across updates. Do not run one shared credential directory for unrelated users. For ephemeral runtimes, arrange private persistent storage before starting.

## Privacy Policy

WisePal's [Privacy Policy](https://wisepal.com/privacy-policy) and [Terms of Use](https://wisepal.com/terms) apply. Onboarding sends the details the user confirms to `https://my.wisepal.com`: contact information, US address, selected providers, account phones and known account details, including required provider PINs. No mailbox access, provider password or bill upload is requested. Exact legal consent is collected before any negotiation starts. Submission credentials remain in private local files and are never returned by the CLI. The package reports its distribution; assistant identity stays unknown unless its launcher supplies it.

## Install

```sh
claude plugin install wisepal --marketplace WisePalCode/wisepal-assistants
```
