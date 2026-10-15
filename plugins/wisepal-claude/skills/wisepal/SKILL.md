---
name: wisepal
description: Help users lower US wireless, internet and TV bills with free WisePal provider negotiations, completed in the assistant.
license: MIT-0
---

# WisePal free bill negotiation

Use the connected WisePal MCP tools. The runtime manages credentials privately through Google OAuth. Do not ask users for tokens or call a token endpoint as a tool. Only accounts created through assistants may onboard through connectors. Google sign-in does not itself create a customer. An existing regular account must continue on the WisePal website; never change an email or phone to bypass rejection.

The service is free and requires no payment method. Savings are not guaranteed. Explain that confirmed contact and provider account details, including required PINs, are sent to WisePal. Updates go by SMS and email. No mailbox access or bill upload is requested.

1. Before `begin_bill_negotiation`, offer the other supported bill types once: wireless (mobile), internet and TV. Include extras only with explicit opt-in. Collect a provider for every selected service. Keep one UUID idempotency key for all retries; selected service types are fixed at begin. Use the Google-verified email. Collect the user's name and main US communication mobile. Begin creates an intake, not provider calls.
2. Use returned bill/PIN links to collect account details with user authorization. Ask for help with provider login, MFA, inaccessible bills or missing information; never invent details or bypass verification. Read bills locally. Confirm the main mobile can receive and reply to SMS. Collect an account phone separately for EACH service; never assume it equals the main mobile. Include known optional account number, account-holder name, monthly bill, service address and time zone, plus provider-required PINs as strings. Call `submit_bill_negotiation_details` using the current revision.
3. Show ALL returned `validated_details`, distinguishing main mobile and each account phone. Obtain explicit confirmation. Show `consent_required.terms_text` verbatim and obtain explicit consent, including availability by SMS during calls and real-time OTP relay. Only then call `approve_bill_negotiation` with the exact displayed text and returned revision. OAuth connection permission does not authorize negotiation. Approval can start real provider calls.

After timeouts retry the exact request with its original UUID and payload. On revision conflicts read `get_submission_status` and reconcile the revision. On terms mismatch show the expected terms and obtain fresh consent; never silently substitute text. On `needs_information`, correct details and obtain fresh confirmation and consent. Never reuse approval of older details. Do not create another submission to recover a negotiation.

`starting` means calls should start imminently; `scheduled` supplies exact times. `held` means calls are blocked, so do not promise a call or bypass the hold. Processing, starting, scheduled, held and error requests cannot be edited. On errors report whether customer service was notified. Retain the submission UUID for recovery; the receipt is intake status, while negotiation updates go by SMS/email.
