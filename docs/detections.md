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

## Detection – Password Spraying Activity

### Detection Objective

Detect repeated failed authentication attempts against multiple Active Directory accounts that may indicate password spraying activity.

### Detection Context

Password spraying is an authentication attack technique in which a single password is attempted against multiple accounts to avoid account lockouts and blend into normal authentication noise.

Unlike brute force attacks that target one account repeatedly, password spraying distributes failed attempts across several users.

### Event Information

| Field | Value |
|---|---|
| Event ID | `4625` |
| Description | An account failed to log on |
| Log Source | Windows Security Event Log |

### Investigation Evidence

Observed failed authentication events for:

- `emma.wilson`
- `alex.brown`

Observed timestamps:

- `21/05/2026 07:06:28 PM`
- `21/05/2026 07:06:47 PM`

Observed failure reason:

```text
Unknown user name or bad password
```

### Investigation Considerations

During triage, analysts should investigate:

- Multiple failed logons across several accounts
- Repeated authentication attempts using similar timing patterns
- Whether authentication attempts originate from the same host or process
- Signs of account enumeration or credential attacks

### MITRE ATT&CK Mapping

```text
T1110.003 – Password Spraying
```