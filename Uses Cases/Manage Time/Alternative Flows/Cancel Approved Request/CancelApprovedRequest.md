## Alternate flow: Cancel Approved Request:

#### Actor

- Employee

#### Goal

- The employee wants to cancel an approved vacation time request.

#### Preconditions

- The employee has a vacation time request that has been
approved and is scheduled for some time in the future or the recent past (pre-
vious 5 business days).

#### Main Flow

1. The employee navigates to the VTS home page through the intranet
portal application, which identifies and authenticates the employee with
the privileges necessary for using the VTS.
2. The VTS home page contains a summary of vacation time requests,
outstanding balance per category of time, and the current status of all
active vacation time requests for the previous 6 months and up to 18
months in the future.
3. The employee selects a vacation time request to cancel, one that is in
the future (or recent past) and has been approved.
4. If the request is in the future, the employee is prompted to confirm the
cancellation. If the request is in the recent past, the employee is
prompted to confirm the cancellation and provide a short explanation. If
the employee approves the cancellation and provides the required infor-
mation, an e-mail notification is sent to the manager, and the state of
the request is changed to canceled. The time allowances used to make
the request are returned to the employee. The employee can also abort
the cancellation, effecting no changes to the current requests.
5. The employee is returned to the main VTS home page. The summaries
are updated to reflect any changes made to the employee’s outstanding
vacation time requests.

#### Flow chart

<img width="605" height="1308" alt="cancel_approved_request_flow_chart" src="https://github.com/user-attachments/assets/6f0a1fc0-72e7-4f9c-b42b-313371f16959" />


#### Sequence diagram

<img width="1061" height="1681" alt="cancel_approved_request_sequence_flow" src="https://github.com/user-attachments/assets/e759e3ae-4e6d-4999-883c-59a1b02b93b9" />


#### Pseudocode

1. Cancel an aproved request
```
BEGIN

    LOGIN TO Intranet Portal
    OPEN VTS

    request = SELECT employee's aproved request

    IF request.status = APPROVED THEN

        IF request.date IS IN future THEN
            ASK employee to confirm cancellation
        ELSE IF request.date IS WITHIN previous 5 business days THEN
            ASK employee to confirm cancellation with explanation
        ELSE
          DISPLAY cancellation invalid message
          RETURN
        END IF

    END IF

    IF cancellation is confirmed THEN
        request.status = CANCELLED
        SAVE request
        RETURN the cancelled vacation allowance to employee
        SEND notification email TO employee's Manager about request cancellation          
    ELSE
        ABORT cancellation request
        No changes to the current request
    END IF

    RETURN to the main VTS page
    DISPLAY updated employee vacation summary

END
```
