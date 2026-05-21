# Detection Notes – Account Lockout Activity (4740)

## Analyst Notes

This detection monitors Active Directory account lockout events generated after repeated failed authentication attempts.

Account lockout activity may indicate authentication abuse, password spraying, brute-force attempts, stale credentials, or user error.

---

## Observed Activity

### Locked Account

- `emma.wilson`

### Observed Event ID

`4740`

### Source System

- `WS01`

### Observed Timestamp

- `21/05/2026 07:25 PM`

---

## Investigation Focus

During triage, analysts should validate:

- Which account was locked
- Which host generated the lockout activity
- Whether repeated failed logons preceded the event
- Whether multiple users experienced lockout activity
- Whether authentication behaviour suggests password spraying or brute-force attempts

---

## Severity

Medium

Escalate severity if:

- Multiple accounts become locked
- Privileged accounts are affected
- Activity originates from unusual systems
- Authentication failures occur across multiple accounts in a short period

---

## MITRE ATT&CK Context

```text
T1110 – Brute Force
```

---

## Investigation Outcome

The investigation confirmed:

- Repeated failed authentication attempts occurred
- Active Directory account lockout policy functioned correctly
- Event ID `4740` telemetry was generated
- Lockout activity originated from `WS01`