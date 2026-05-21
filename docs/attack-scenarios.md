## Scenario 1 – Security Group Membership Change Monitoring

### Objective

Monitor and investigate Active Directory security group membership modifications.

### Scenario

A domain administrator added `john.smith` to the `Finance_Users` security group to simulate monitoring of privileged access modifications in an enterprise Active Directory environment.

### Event Observed

| Event ID | Description |
|---|---|
| `4728` | A member was added to a security-enabled global group |

### Outcome

The event was successfully generated and validated, confirming visibility into Active Directory permission and group membership changes.

## Scenario 2 – Password Spraying Detection

### Objective

Simulate and investigate failed authentication activity consistent with password spraying behaviour in an Active Directory environment.

### Scenario

Multiple failed authentication attempts were generated against domain user accounts using the same incorrect password to simulate a password spraying pattern.

The activity targeted:

- `emma.wilson`
- `alex.brown`

The authentication failures were generated against the Active Directory domain and validated through Windows Security logs on the Domain Controller (`DC01`).

### Timeline

| Timestamp | Activity |
|---|---|
| `21/05/2026 07:06 PM` | Failed authentication activity generated |
| `21/05/2026 07:06 PM` | Windows Security logs investigated |

### Event Observed

| Event ID | Description |
|---|---|
| `4625` | An account failed to log on |

### Outcome

The scenario successfully generated failed Active Directory authentication telemetry and validated visibility into suspicious authentication activity through Windows Security logs.