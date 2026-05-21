## Detection – Security Group Membership Change

### Detection Objective

Monitor Active Directory security group membership modifications that may indicate unauthorised access changes, privilege abuse, or administrative misuse.

### Event Information

| Field | Value |
|---|---|
| Event ID | `4728` |
| Description | A member was added to a security-enabled global group |
| Log Source | Windows Security Event Log |

### Why This Matters

Unexpected group membership modifications may indicate:

- Privilege misuse
- Insider activity
- Compromised administrative accounts
- Unauthorised permission assignment

### Investigation Example

Observed:

- `john.smith` added to `Finance_Users`
- Action performed by `Administrator`
- Event successfully captured in Windows Security logs