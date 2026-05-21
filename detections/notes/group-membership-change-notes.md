# Detection Notes – Group Membership Change (4728)

## Analyst Notes

This detection monitors modifications to Active Directory security-enabled groups.

### Observed Activity

- User added: `john.smith`
- Security group: `Finance_Users`
- Performed by: `Administrator`

### Event ID

`4728`

### Investigation Focus

During triage, analysts should validate:

- Whether the change was authorised
- Whether the affected group is sensitive or privileged
- Whether the administrator account activity appears expected
- Timing and surrounding authentication activity

### Severity

Medium

### MITRE ATT&CK Relevance

Privilege Escalation / Persistence (context dependent)