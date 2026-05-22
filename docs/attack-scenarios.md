## Scenario 1 – Security Group Membership Change Monitoring

### Objective

Monitor and investigate Active Directory security group membership modifications.

### Scenario

A domain administrator added `john.smith` to the `Finance_Users` security group to simulate monitoring of privileged access modifications in an enterprise Active Directory environment.

### Event Observed

| Event ID | Description                                           |
| -------- | ----------------------------------------------------- |
| `4728`   | A member was added to a security-enabled global group |

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

| Timestamp             | Activity                                 |
| --------------------- | ---------------------------------------- |
| `21/05/2026 07:06 PM` | Failed authentication activity generated |
| `21/05/2026 07:06 PM` | Windows Security logs investigated       |

### Event Observed

| Event ID | Description                 |
| -------- | --------------------------- |
| `4625`   | An account failed to log on |

### Outcome

The scenario successfully generated failed Active Directory authentication telemetry and validated visibility into suspicious authentication activity through Windows Security logs.

## Scenario 3 – Account Lockout Investigation

### Objective

Simulate and investigate account lockout activity caused by repeated failed authentication attempts within an Active Directory environment.

### Scenario

Repeated failed authentication attempts were generated against the domain account `emma.wilson` until the account lockout threshold was reached.

The activity originated from:

```text
WS01
```

The lockout event was validated and investigated through Windows Security logs on the Domain Controller (`DC01`).

### Timeline

| Timestamp             | Activity                                            |
| --------------------- | --------------------------------------------------- |
| `21/05/2026 07:25 PM` | Repeated failed authentication attempts generated   |
| `21/05/2026 07:25 PM` | Account lockout observed                            |
| `21/05/2026 07:25 PM` | Lockout event investigated in Windows Security logs |

### Event Observed

| Event ID | Description                   |
| -------- | ----------------------------- |
| `4740`   | A user account was locked out |

### Outcome

The scenario successfully generated account lockout telemetry and validated visibility into authentication abuse activity through Windows Security logs.

## Scenario 4 – Active Directory Reconnaissance Investigation

### Objective

Simulate and investigate Active Directory reconnaissance activity performed using authenticated domain credentials.

### Scenario

Authenticated reconnaissance activity was performed from a Kali Linux system against the Active Directory Domain Controller (`DC01`) using valid domain credentials.

The activity included:

- Domain user enumeration
- Domain group enumeration

The reconnaissance originated from:

```text
KALI (192.168.100.5)
```

The authenticated activity used:

```text
ADSOC\john.smith
```

Windows Security logs were investigated to validate authentication telemetry associated with the reconnaissance activity.

### Timeline

| Timestamp             | Activity                                      |
| --------------------- | --------------------------------------------- |
| `22/05/2026 05:34 PM` | Anonymous SMB enumeration attempt observed    |
| `22/05/2026 05:39 PM` | Authenticated domain reconnaissance performed |
| `22/05/2026 05:39 PM` | Security log investigation completed          |

### Event Observed

| Event ID | Description      |
| -------- | ---------------- |
| `4624`   | Successful logon |

### Outcome

The scenario successfully simulated authenticated Active Directory reconnaissance and validated visibility into authentication telemetry generated from a non-Windows system (`KALI`) against the Domain Controller.
