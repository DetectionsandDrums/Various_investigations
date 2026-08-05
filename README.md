# Investigations

A collection of documented scam, fraud, and social-engineering investigations.
Each case captures the actor's approach, indicators of compromise (IOCs),
tactics/techniques (TTPs), and preserved evidence, published for
security-awareness purposes and so others targeted by the same actors can
cross-reference the indicators.

---

## Purpose

- Document real-world social-engineering and fraud attempts encountered in the wild.
- Preserve indicators (accounts, addresses, domains, message metadata) so recurring
  actors and campaigns can be cross-referenced.
- Break down each case into a repeatable structure: narrative -> IOCs -> TTPs -> red
  flags -> evidence.
- Provide practical guidance for anyone targeted by the same lure.

---

## Cases

| # | Case | Type | Platform | Status |
|---|---|---|---|---|
| 01 | [LinkedIn Recruiter Scam](./LinkedIn_recruiter_scam/) | Recruitment / off-platform handoff | LinkedIn | Documented |
| 02 | [Email Recruitment Scam](./recruiter_email_scam/) | Recruitment / fraudulent hiring | Email | Documented |

> Add new cases as rows here and link to the case directory.

---

## Repository structure

```
investigations/
├── README.md                       # this file
├── LinkedIn_recruiter_scam/
│   ├── README.md                   # case write-up
│   └── evidence/                   # screenshots, headers, etc.
└── recruiter_email_scam/
    ├── README.md
    └── evidence/
```

Each case lives in its own directory with a self-contained `README.md` and an
`evidence/` folder.

---

## Case write-up template

Each case `README.md` follows the same structure:

- **Summary** — one-table overview (threat type, platform, persona, status).
- **Indicators of Compromise (IOCs)** — identity indicators, handoff indicators,
  message/email metadata. Defang live addresses and domains
  (e.g., `bad[at]example[.]com`, `evil[.]com`).
- **Attack narrative** — the numbered step-by-step chain of the interaction.
- **Red flags / TTPs** — the tells and techniques, so the pattern is recognizable.
- **If you were contacted** — practical reporting and containment guidance.
- **Evidence** — an index mapping each file to its stage in the interaction.
- **Disclaimer** — good-faith notice; names on scam accounts may be fabricated,
  compromised, or impersonating real, uninvolved people.

---

## Conventions

- **Defang indicators.** Email addresses, URLs, and domains are defanged so they are
  not live/clickable in the repo.
- **Preserve metadata.** Notification-email tokens and message IDs are retained where
  present — they let platforms locate a thread server-side even after an account is
  deleted.
- **Name ordering.** Evidence files are named to reflect their order in the actual
  interaction (e.g., `01-outreach.png`), independent of upload order.
- **Good faith.** Cases are published for awareness. Indicators are for
  cross-referencing only; no conclusion should be drawn about any real individual who
  happens to share a name with a scam account.

---

## Disclaimer

This repository documents individual reported interactions and is published in good
faith for security-awareness purposes. Names, accounts, and addresses associated with
scams may be fabricated, compromised, or used to impersonate real and uninvolved
people. Nothing here should be read as an accusation against any real individual.
Indicators are shared solely so others can recognize and cross-reference the same
tactics.
