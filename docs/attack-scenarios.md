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