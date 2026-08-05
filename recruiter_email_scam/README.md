# Recruiter Scam — Advance-Fee Job-Placement Fraud

Raw email samples and analysis of an advance-fee recruitment scam, shared publicly for defender awareness and threat-intelligence purposes.

This is a **job-seeker-pays** recruitment scam: the operator poses as a recruiter, builds rapport with a job seeker, then demands full upfront payment before performing any "job search campaign" work. No legitimate recruiter charges the candidate — the hiring employer pays the recruiter's fee. A request for the job seeker to pay upfront is the defining signature of this fraud.

## Contents

- Raw email samples (`.eml` / `.txt`) captured during the engagement
- Analysis notes and indicators of compromise (below)
- Detection content — *coming soon* (see [Detections](#detections))

## ⚠️ On the samples

The email samples in this folder have been **sanitized to remove the recipient's personal information** (recipient email address, originating IP, and any personal identifiers in the header chain). The sender's infrastructure — from address, sending domain, and authentication results — is preserved intact, as that is the shareable threat-intel value.

If you fork or reuse these samples, they are provided as-is for research and defensive use only.

## What happened

1. **Initial contact** arrived from a recruiter-branded email address that failed domain alignment — Gmail displayed a `via gmail.com` indicator, meaning the message authenticated as a generic Gmail account rather than the corporate-looking domain in the `From` field.
2. **Rapport building** — standard recruiter language, offers to review and optimize the resume, promises of recruiter outreach and interview opportunities.
3. **The ask** — an email requesting **full upfront payment** before any work would begin, framed as an "investment" in a personalized job-search campaign, with vague and unmeasurable deliverables and reassurances of "no hidden fees."
4. No employer, no specific role, and no verifiable contract were provided before payment was demanded.

## Red flags (the pattern)

- **Payment flows the wrong direction.** The job seeker is asked to pay. Legitimate recruiters are paid by employers.
- **Upfront payment before any work**, before verification, before an enforceable agreement.
- **Authentication mismatch** — `via gmail.com` on a message presented as coming from a corporate recruiting domain. The `From` domain does not match the authenticated sending domain.
- **Generic, recruiting-themed domain** with no verifiable company behind it.
- **Sender name** does not correspond to any verifiable corporate persona.
- **Vague, unmeasurable deliverables** — "strategic positioning," "recruiter outreach," "maximize interview opportunities" — with no named employer or concrete commitment.
- **Preemptive trust reassurance** — insisting "no hidden fees" before any question of fees was raised.
- **Manufactured urgency** — "I'll begin immediately once payment is confirmed."

## Indicators of Compromise (IOCs)

> Indicators are **defanged**. Re-fang before use in tooling.

| Type | Indicator | Notes |
|------|-----------|-------|
| Email (sender) | `mashoodsekinat@executivecareersconnect[.]com` | Claimed recruiter address |
| Domain | `executivecareersconnect[.]com` | Recruiter-themed sender domain |
| Sending infrastructure | Gmail (`via gmail.com`) | `From` domain ≠ authenticated sending domain |
| Behavioral | Upfront-payment demand from job seeker | Advance-fee recruitment fraud |

*See the raw samples for full headers and message bodies.*

## Detections

Detection content for this activity will be added here. Planned coverage:

- **Inbound authentication mismatch** — `From` display domain is a custom/corporate-looking domain while the authenticated sending domain (DKIM `d=`) is a free provider (e.g. gmail.com).
- **DMARC fail/none on first-contact external sender** — no prior mail history from the sending domain.
- **Advance-fee lure heuristics** — payment-solicitation language layered on top of the authentication signals to control false positives.
- **Newly-registered sender domain** — enrichment against domain registration age, flagging first contact from recently-registered domains.

Formats planned: Sigma (portable) and KQL (Microsoft Sentinel / Defender `EmailEvents`).

## If you've been targeted

- **Do not pay anything** — no deposit, no reduced rate, no "just the resume fee."
- **Do not send money or financial details.** Legitimate recruiters never charge the candidate.
- **Report it.** In the US: the FTC at [reportfraud.ftc.gov](https://reportfraud.ftc.gov), and your email provider's phishing report function (in Gmail: **Report phishing**, not just "Report spam").
- **Preserve evidence** — keep the full thread and export the raw headers before the account is suspended.

## Disclaimer

Shared for educational, awareness, and defensive security research purposes. The indicators reflect a single observed campaign and may change. This repository does not accuse any named individual of a crime; the addresses and domains published here are the infrastructure observed in the fraudulent messages.
