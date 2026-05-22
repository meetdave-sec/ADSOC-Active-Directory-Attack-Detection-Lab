# Detection Notes – Active Directory Reconnaissance Activity

## Analyst Notes

This detection monitors authenticated Active Directory reconnaissance activity performed using valid domain credentials.

After obtaining access to a domain account, attackers commonly enumerate users, groups, and privileged relationships to understand domain structure and identify opportunities for privilege escalation or lateral movement.

---

## Observed Activity

### Authenticated Account

- `john.smith`

### Source System

- `KALI`

### Source IP Address

- `192.168.100.5`

### Observed Event ID

`4624`

### Observed Timestamp

- `22/05/2026 05:39 PM`

### Reconnaissance Activity

- `enumdomusers`
- `enumdomgroups`

---

## Investigation Focus

During triage, analysts should validate:

- Which account authenticated successfully
- Whether authentication originated from expected systems
- Whether a non-Windows system authenticated to Active Directory
- Whether domain user/group enumeration followed authentication
- Whether privileged groups were enumerated
- Signs of privilege escalation preparation or lateral movement planning

---

## Severity

Medium

Escalate severity if:

- Privileged accounts perform reconnaissance unexpectedly
- Authentication originates from unknown or unmanaged hosts
- Enumeration activity increases significantly
- Reconnaissance is followed by privilege escalation attempts

---

## MITRE ATT&CK Context

```text
T1087 – Account Discovery
T1069 – Permission Group Discovery
```

---

## Investigation Outcome

The investigation confirmed:

- Successful authentication using valid domain credentials
- Authentication originated from `KALI (192.168.100.5)`
- User enumeration activity occurred
- Group enumeration activity occurred
- Windows Security Event ID `4624` telemetry was generated and investigated