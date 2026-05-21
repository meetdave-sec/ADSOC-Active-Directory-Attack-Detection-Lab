# Detection Notes – Password Spraying Activity (4625)

## Analyst Notes

This detection monitors repeated failed authentication attempts across multiple Active Directory accounts that may indicate password spraying activity.

Unlike brute-force attacks that repeatedly target a single account, password spraying distributes failed authentication attempts across several users using the same password.

---

## Observed Activity

### Targeted Accounts

- `emma.wilson`
- `alex.brown`

### Observed Event ID

`4625`

### Observed Timestamps

- `21/05/2026 07:06:28 PM`
- `21/05/2026 07:06:47 PM`

### Failure Reason

```text
Unknown user name or bad password
```

---

## Investigation Focus

During triage, analysts should validate:

- Multiple failed logons across several accounts
- Similar timing between authentication attempts
- Whether the activity originated from the same host or process
- Signs of credential abuse or account enumeration
- Whether account lockouts later occurred

---

## Severity

Medium

Escalate severity if:

- Authentication attempts increase significantly
- Sensitive or privileged accounts are targeted
- Activity originates from suspicious hosts
- Account lockouts are observed

---

## MITRE ATT&CK Mapping

```text
T1110.003 – Password Spraying
```