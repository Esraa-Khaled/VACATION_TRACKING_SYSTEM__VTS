## Alternate flow: Withdraw Request

#### Actor:
- Employee

#### Goal: 
- The employee wants to withdraw an outstanding request for vacation time.
Preconditions: An employee has made a vacation time request, and that
request has yet to be approved or denied by an authorized manager. See also

#### Preconditions:
-  An employee has made a vacation time request, and that
request has yet to be approved or denied by an authorized manager. See also
main flow preconditions.

#### Main flow:
1. The employee navigates to the VTS home page through the intranet
portal application, which identifies and authenticates the employee with
the privileges necessary for using the VTS.
2. The VTS home page contains a summary of vacation time requests,
outstanding balances per category of time, and the current status of all
active vacation time requests for the previous 6 months and up to 18
months in the future.
3. The employee selects a vacation time request to withdraw, one that is
currently pending approval.
4. The VTS prompts the employee to confirm the request to withdraw the
previously submitted vacation time request.
5. The employee confirms the desire to withdraw, and the request is
removed from the manager’s list of pending approvals.
6. The system sends a notification e-mail to the manager.
7. The system updates the request state to withdrawn.

#### Pseudocode

1. Withdrawn a pending request
```
BEGIN

    LOGIN TO Intranet Portal
    OPEN VTS

    request = SELECT employee's pending request

    IF request.status = PENDING_APPROVAL THEN

        DISPLAY request details
        ASK employee to confirm withdrawal

        IF employee confirms withdrawal THEN

            request.status = WITHDRAWN
            SAVE request

            REMOVE request FROM manager's pending approvals list

            SEND notification email TO employee's Manager for request withdrawal

        END IF

    END IF

    RETURN to the main VTS page
    DISPLAY updated employee vacation summary

END
```
