# Privileged Group Membership Change Investigation Report

## Overview

This report documents the investigation of a privileged Active Directory security group membership change generated within the ADSOC lab environment.

The objective was to validate visibility into privileged access modifications and investigate Windows Security telemetry associated with changes to high-value administrative groups.

---

## Investigation Metadata

| Field                | Value                                                    |
| -------------------- | -------------------------------------------------------- |
| Investigation Date   | `22/05/2026`                                             |
| Investigation Time   | `06:21 PM`                                               |
| Domain Controller    | `DC01`                                                   |
| Domain               | `adsoc.local`                                            |
| Detection Type       | Privileged Group Membership Change                       |
| MITRE ATT&CK Context | `T1098 – Account Manipulation`, `T1078 – Valid Accounts` |

---

## Scenario Summary

A domain account was added to a privileged Active Directory security group to simulate privilege escalation behaviour.

The following account was added:

```text
john.smith
```

The following privileged group was modified:

```text
Domain Admins
```

The investigation validated privileged access modification telemetry through Windows Security logs on the Domain Controller.

---

## Detection Details

| Field       | Value                                                 |
| ----------- | ----------------------------------------------------- |
| Event ID    | `4728`                                                |
| Description | A member was added to a security-enabled global group |
| Log Source  | Windows Security Event Log                            |

Observed account added:

```text
john.smith
```

Observed privileged group:

```text
Domain Admins
```

Observed timestamp:

```text
22/05/2026 06:21 PM
```

---

## Investigation Timeline

| Timestamp             | Event                                      |
| --------------------- | ------------------------------------------ |
| `22/05/2026 06:21 PM` | `john.smith` added to `Domain Admins`      |
| `22/05/2026 06:21 PM` | Privileged group modification investigated |

---

## Investigation Findings

The investigation confirmed:

- A privileged Active Directory group was modified
- The account `john.smith` was added to `Domain Admins`
- Event ID `4728` telemetry was generated
- Windows Security logs successfully recorded privileged access changes
- The activity aligned with privilege escalation monitoring use cases

---

## Evidence

### Event ID 4728 – Domain Admins Membership Change

![Domain Admin Membership Change](../screenshots/domain-admin-membership-change-4728.png)

---

## Analyst Notes

During triage, analysts should investigate:

- Who performed the privileged group modification
- Whether the change was approved or expected
- Whether the affected account should possess administrative privileges
- Whether additional privileged groups were modified
- Signs of persistence or privilege escalation activity

---

## Conclusion

This investigation validated visibility into privileged Active Directory group membership changes and demonstrated a SOC investigation workflow for monitoring privileged access modification activity through Windows Security telemetry.
