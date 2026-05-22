## Detection – Security Group Membership Change

### Detection Objective

Monitor Active Directory security group membership modifications that may indicate unauthorised access changes, privilege abuse, or administrative misuse.

### Event Information

| Field       | Value                                                 |
| ----------- | ----------------------------------------------------- |
| Event ID    | `4728`                                                |
| Description | A member was added to a security-enabled global group |
| Log Source  | Windows Security Event Log                            |

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

| Field       | Value                       |
| ----------- | --------------------------- |
| Event ID    | `4625`                      |
| Description | An account failed to log on |
| Log Source  | Windows Security Event Log  |

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

## Detection – Account Lockout Activity

### Detection Objective

Detect and investigate account lockout activity caused by repeated failed authentication attempts against Active Directory accounts.

### Detection Context

Account lockout activity may indicate:

- Password spraying attempts
- Brute-force authentication attempts
- Misconfigured services or stale credentials
- Repeated user authentication failures

Monitoring lockout events helps analysts identify suspicious authentication behaviour and determine whether failed authentication activity escalated into account access disruption.

### Event Information

| Field       | Value                         |
| ----------- | ----------------------------- |
| Event ID    | `4740`                        |
| Description | A user account was locked out |
| Log Source  | Windows Security Event Log    |

### Investigation Evidence

Observed locked account:

- `emma.wilson`

Observed source system:

- `WS01`

Observed timestamp:

- `21/05/2026 07:25 PM`

### Investigation Considerations

During triage, analysts should investigate:

- Which account was locked
- Which host generated the activity
- Whether repeated failed logons preceded the lockout
- Whether authentication failures targeted multiple users
- Signs of password spraying or brute-force behaviour

### MITRE ATT&CK Context

```text
T1110 – Brute Force
```

## Detection – Active Directory Reconnaissance Activity

### Detection Objective

Detect and investigate authenticated Active Directory reconnaissance activity performed using valid domain credentials.

### Detection Context

After obtaining valid credentials, attackers commonly perform reconnaissance against Active Directory to enumerate:

- Domain users
- Security groups
- Privileged groups
- Administrative relationships

This activity helps attackers understand domain structure and identify high-value targets for privilege escalation or lateral movement.

### Event Information

| Field       | Value                                 |
| ----------- | ------------------------------------- |
| Event ID    | `4624`                                |
| Description | An account was successfully logged on |
| Log Source  | Windows Security Event Log            |

### Investigation Evidence

Observed account:

- `john.smith`

Observed source system:

- `KALI`

Observed source IP:

- `192.168.100.5`

Observed timestamp:

- `22/05/2026 05:39 PM`

Observed reconnaissance activity:

- `enumdomusers`
- `enumdomgroups`

### Investigation Considerations

During triage, analysts should investigate:

- Which account authenticated successfully
- Whether authentication originated from expected systems
- Whether non-Windows systems authenticated to the Domain Controller
- Whether user/group enumeration occurred after authentication
- Signs of privilege discovery or lateral movement preparation

### MITRE ATT&CK Context

```text
T1087 – Account Discovery
T1069 – Permission Group Discovery
```
