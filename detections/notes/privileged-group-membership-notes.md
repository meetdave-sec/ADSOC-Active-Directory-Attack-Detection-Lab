# Detection Notes – Privileged Group Membership Change (4728)

## Analyst Notes

This detection monitors membership changes to privileged Active Directory security groups that may indicate unauthorized privilege escalation, administrative abuse, or persistence activity.

Attackers commonly attempt to obtain elevated privileges by adding accounts to high-value administrative groups after gaining access to a domain environment.

---

## Observed Activity

### Account Added

- `john.smith`

### Privileged Group Modified

- `Domain Admins`

### Observed Event ID

`4728`

### Observed Timestamp

- `22/05/2026 06:21 PM`

---

## Investigation Focus

During triage, analysts should validate:

- Who performed the privileged group modification
- Whether the membership change was authorized
- Whether the affected account should possess privileged access
- Whether additional administrative groups were modified
- Whether the activity indicates persistence or privilege escalation

---

## Severity

High

Escalate severity if:

- Privileged groups such as `Domain Admins` or `Enterprise Admins` are modified unexpectedly
- Newly added accounts are low-privileged or unusual users
- Multiple privileged groups are modified within a short time period
- Additional suspicious authentication or administrative activity follows

---

## MITRE ATT&CK Context

```text
T1098 – Account Manipulation
T1078 – Valid Accounts
```

---

## Investigation Outcome

The investigation confirmed:

- A privileged Active Directory group membership change occurred
- `john.smith` was added to `Domain Admins`
- Event ID `4728` telemetry was generated and investigated
- Windows Security logs successfully recorded privileged access modification activity