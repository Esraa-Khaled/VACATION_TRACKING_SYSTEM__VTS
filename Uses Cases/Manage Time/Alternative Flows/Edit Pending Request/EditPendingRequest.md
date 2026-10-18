## Alternate flow: Edit Pending Request:

#### Actor:
- Employee

#### Goal: 
- The employee wants to edit the description or title of a pending request.

#### Preconditions.
- An employee has made a vacation time request, and that
request has yet to be approved or denied by an authorized manager. See also
main flow preconditions.

#### Main Flow:

1. The employee navigates to the VTS home page through the intranet
portal application, which identifies and authenticates the employee with
the privileges necessary for using the VTS.
2. The VTS home page contains a summary of vacation time requests,
outstanding balances per category of time, and the current status of all
active vacation time requests for the previous 6 months and up to 18
months in the future.
3. The employee selects a request to edit, one that is pending approval.
4. The VTS displays an editable view of the request. The employee is
allowed to change the title, comments, or dates. The employee can also
choose to delete or withdraw this request.
5. The employee changes request information and submits the changes to
the system.
6. If the employee withdraws the request, the VTS prompts for confirma-
tion before withdrawing the request. If changes are made only to the
information, the changes are accepted, and the screen returns to the
main VTS home page. If there are errors or problems with the informa-
tion changes, the VTS redisplays the editing page and highlights and
explains all problems.

#### Pseudocode

1. Edit a pending request
```
BEGIN

    LOGIN TO Intranet Portal
    OPEN VTS

    request = SELECT employee's pending approval request

    IF request.status = PENDING_APPROVAL THEN

        DISPLAY request details
        DISPLAY Valid Actions:
          - EDIT_REQUEST
          - DELETE_REQUEST
          - WITHDRAW_REQUEST

        employeeSelectedAction = SELECT action
        
        IF employeeSelectedAction = EDIT_REQUEST THEN
            request.tile = ENTER the new title
            request.comments = ENTER the new comments
            request.dates = ENTER the new dates

            validationResult = VALIDATE request after update

            IF validationResultis VALID THEN
                SAVE the updated request
                RETURN
                DISPLAY updated employee vacation summary
            ELSE
                DISPLAY validation errors
                BACK to the edit page to correctrequest
                RETURN
            END IF

        ELSE IF employeeSelectedAction = DELETE_REQUEST THEN
            DELETE request

        ELSE IF employeeSelectedAction = WITHDRAW_REQUEST THEN
            EXECUTE withdraw a pending request flow
        END IF

    END IF


    RETURN to the main VTS page
    DISPLAY updated employee vacation summary

END
```
