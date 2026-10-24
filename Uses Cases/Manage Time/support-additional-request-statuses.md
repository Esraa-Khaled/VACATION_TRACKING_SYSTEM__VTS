# Supporting Additional Request Statuses

## Requirements

- Support future request statuses such as `HR_PENDING`, `HR_APPROVED`, and other workflow stages with minimal changes.
- Avoid modifying the main workflow implementation whenever a new status or approval stage is introduced.


### Design Approach

1. **Request Status Management**

   Use a separate `REQUEST_STATUS` table instead of hard-coded ENUM values to manage request statuses at the database level.

   This allows new statuses to be introduced without modifying the existing `REQUEST` table structure.

2. **Request Status Transition Management**

   Adding a new status alone is not sufficient to support workflow extensions.

   Introduce a `REQUEST_WORKFLOW_TRANSITION` table to define:
   - The current status.
   - The target status.
   - The action performed.
   - The role responsible for performing the transition.

   This table defines the allowed transitions between request statuses and the roles authorized to perform them.

   When new workflow stages are required, the corresponding statuses and transitions can be configured through the database, minimizing changes to the existing workflow implementation.

### Example Request Statuses

| Status | Description |
|---|---|
| PENDING_APPROVAL | Waiting for manager approval |
| APPROVED | Request approved |
| REJECTED | Request rejected |
| CANCELED | Request canceled |
| WITHDRAWN | Request withdrawn |
| HR_PENDING | Waiting for HR approval |
| HR_APPROVED | Approved by HR |

### Example Request Status Transitions

| Action | From Status | To Status | Role |
|---|---|---|---|
| APPROVE | PENDING_APPROVAL | APPROVED | Manager |
| REJECT | PENDING_APPROVAL | REJECTED | Manager |
| WITHDRAW | PENDING_APPROVAL | WITHDRAWN | Employee |
| SEND_TO_HR | PENDING_APPROVAL | HR_PENDING | Manager |
| CANCEL | APPROVED | CANCELED | Employee |
| HR_APPROVE | HR_PENDING | HR_APPROVED | HR |
| HR_REJECT | HR_PENDING | REJECTED | HR |

### Request state machine

<img width="799" height="606" alt="Request_state_machine" src="https://github.com/user-attachments/assets/c44bc8d9-57e1-4cee-a7e9-47d3c8888524" />

### Entity Diagram

<img width="1133" height="1043" alt="ERD" src="https://github.com/user-attachments/assets/86e9e943-dfae-46b6-9213-368aee6aebc6" />

---

> When you add a new status like ``MEDICAL_REVIEW_PENDING``, ``MEDICAL_APPROVED`` you only need to:
> 1. Insert the new status into REQUEST_STATUS.
> 2. Insert the allowed transitions into REQUEST_WORKFLOW_TRANSITION.
> 3. Configure the responsible role.
> The existing REQUEST table remains unchanged.
