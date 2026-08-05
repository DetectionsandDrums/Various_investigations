# LinkedIn Recruitment Scam — IOC Record

Documentation of a LinkedIn recruitment/off-platform-handoff scam. The scammer
initiated contact via LinkedIn messaging under a recruiter persona, then attempted
to move the conversation off-platform to a free email address disguised as a
"Microsoft Teams account." The profile was deleted shortly after the handoff,
a common evidence-destruction step.

This record is published for awareness and so others targeted by the same actor
can cross-reference the indicators.

---

## Summary

| Field | Value |
|---|---|
| **Threat type** | Recruitment scam / off-platform handoff |
| **Platform** | LinkedIn (InMail / messaging) |
| **Persona** | Recruiter ("Recruitment Assistant \| Executive Search Support") |
| **Handoff pretext** | Fake "Microsoft Teams account" (actually a free Gmail address) |
| **Profile status** | Deleted (404) after contact |
| **Target profile** | Cybersecurity / detection engineering professional |

---

## Indicators of Compromise (IOCs)

### Identity indicators
| Indicator | Value |
|---|---|
| Display name | Matias Capece |
| Claimed role | Recruitment Assistant \| Executive Search Support \| Talent Research & Candidate Engagement |
| Profile slug | `matias-capece` |
| Canonical URL | `https://www.linkedin.com/in/matias-capece` (now 404) |

### Handoff indicator
| Indicator | Value |
|---|---|
| "Teams" email (defanged) | `bjcb395[at]gmail[.]com` |
| Email provider | Gmail (free webmail — **not** a Microsoft Teams / org account) |

### Message metadata (from LinkedIn notification email)
These are tied to the specific message thread and can help LinkedIn Trust & Safety
locate the conversation server-side even after profile deletion.

| Field | Value |
|---|---|
| `midToken` | `AQFn3-GRvtxlAw` |
| `midSig` | `0O4lBVUeieaYo1` |
| `eid` | `i17gk-msf0ozh6-jk` |
| InMail type | `email_hire_inmail_reply_to_member` |

---

## Attack narrative

1. **Cold outreach.** Unsolicited message from a "recruiter" persona praising the
   target's background and proposing to connect about a vague opportunity.
2. **Sector-specific lure.** The "opportunity" was described as an early-stage
   technology project in cybersecurity, infrastructure protection, and advanced
   technology integration — language mirrored back from the target's own profile
   (threat detection, SIEM engineering, MITRE ATT&CK, threat hunting, CTI) to build
   false rapport.
3. **Introduce the "employer."** The recruiter offered to introduce an employer who
   would share "project vision, technical requirements, and role details."
4. **Force text-only, off-platform contact.** Claimed the employer is a non-native
   English speaker from Europe and therefore prefers text-based chat on Teams, Signal,
   or WhatsApp — a pretext to avoid a video call that would expose the impersonation.
5. **The handoff.** Provided a free Gmail address (`bjcb395[at]gmail[.]com`) framed as
   the employer's "Teams account."
6. **Evidence destruction.** The LinkedIn profile was deleted shortly after the
   handoff.

---

## Red flags / TTPs

- **Recruiter → "employer" relay.** A "talent" persona hands you to a second party
  who does the real pitch, adding a layer of separation.
- **"Teams account" that is a Gmail address.** Microsoft Teams uses organizational or
  Microsoft accounts, not arbitrary free webmail. A "Teams account" that is a Gmail
  address is a contradiction and the clearest tell here.
- **Text-only justification.** The "non-native English speaker, please only text" line
  is a scripted excuse to avoid live voice/video that would break the impersonation.
- **Rapid push off-platform.** Moving you to Teams/Signal/WhatsApp escapes LinkedIn's
  moderation and reporting surface.
- **Profile deletion post-contact.** Destroys the primary evidence and hinders
  reporting.
- **Profile mirroring.** The pitch reflected the target's exact skill keywords, a sign
  of automated or templated targeting rather than a genuine match.

---

## If you were contacted by this actor

- **Do not** email the handoff address or continue the conversation off-platform.
- **Report from the message thread**, not the profile: open the conversation in your
  LinkedIn inbox → **Report** → **Scam or fraud**. The thread persists in your inbox
  even though the profile is deleted.
- **Preserve the notification email.** The `midToken` / `eid` values above let LinkedIn
  locate the thread server-side.
- Recover the clean profile slug from the notification email by stripping the `/comm`
  path segment and all tracking parameters (`lipi`, `midToken`, `midSig`, `trk`,
  `trkEmail`, `eid`).

---

## Evidence

Screenshots of the full exchange are included in this repository.

| File | Contents |
|---|---|
| `1.png` | Handoff message — the "Teams account" Gmail address is provided |
| `2.png` | Recruiter offers to introduce the "employer"; text-only justification begins |
| `3.png` | Opening pitch — cybersecurity "opportunity" mirroring the target's skills |
| `4.png` | Initial cold outreach and the (now-deleted) profile header |

---

## Disclaimer

This record documents a single reported interaction and is published in good faith
for security-awareness purposes. The name "Matias Capece" appeared on a LinkedIn
profile used to make contact; the account may be fabricated, compromised, or
impersonating a real person, and no conclusion should be drawn about any real
individual of that name. Indicators are shared for cross-referencing only.
