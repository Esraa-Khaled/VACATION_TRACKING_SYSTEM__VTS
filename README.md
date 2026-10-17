# Vacation Tracking System (VTS)



## Vision
A Vacation Tracking System (VTS) will provide individual employees with the
capability to manage their own vacation time, sick leave, and personal time off,
without having to be an expert in company policy or the local facility’s leave
policies.
The main goal of this application is to improve the internal business processes of
this organization, at least with respect to the time it takes to manage vacation time
requests. 

## Requirments:
#### Functional Requirments (FR)
| ID    | Requirement                                |
| ------|-----------------------------------------|
| FR-1  | Implements a flexible rules-based system for validating and verifying leaves | 
| FR-2  | Enables manager approval (optional)      | 
| FR-3  | Display the past requests      | 
| FR-4  | Allow requests to be made up to a year and a half in the future|
| FR-5  | Uses e-mail notifications for manager approval and notify employees with the request status changes|
| FR-6  | Keeps activity logs for all transactions |
| FR-7  | HR and system administrator can override all actions restricted by rules, with logging of those actions|
| FR-8  | Allows managers to directly award personal leave time (with system-set limits)|
| FR-9  | Provides a Web service interface for other internal systems to query employee’s vacation request summary|
| FR-10 | Interface with the HR department legacy systems to retrieve employee information and changes |


#### Non-functional Requirments (NFR)
| ID     | Requirement |
|--------|-------------|
| NFR-1  | Uses existing hardware and middleware |
| NFR-2  | For presentation tier: Java Server Pages (JSP), Servlets, and Java Server Faces (JSF) |
| NFR-3  | For Business tier: Enterprise Java Beans (EJB) 2.x (specifically, Container Managed Persistence [CMP] beans for entities, and session beans for controllers), and Service Data Objects (SDO) |
| NFR-4  | Security: Central Authentication Service (CAS), uses the portal’s single-sign-on mechanisms for all authentication |
| NFR-5  | Implement an intuitive user interface that has a quick response and is easy to navigate |
| NFR-6  | The interface should not have any dependencies on specific browser versions or features, and should behave properly on all standard HTML 3.2-capable browsers |
| NFR-7 | Back Up System Logs|
 

## Constraints / Rules:

* An employee can’t take more than X consecutive days of leave for Y type of
grant.
* Vacation time of type X cannot be taken when directly adjacent to a com-
pany or location-specific holiday.
* Vacation time of type X is limited to Y hours per week or month.
* Vacation time may not be granted when there are only X number of employ-
ees scheduled to work from the list Y of employees.
* Vacation time may not be granted on these dates: X.
* Vacation time of this type is limited to certain days of the week: {M, T, W,
Th, F, Sat, Sun}.

## Domain


## Actors:
1. **Employee:** The main user of this system. An employee uses this system to
manage his or her vacation time.
2. **Manager:** An employee who has all the abilities and goals of a regular
employee, but with the added responsibility of approving vacation requests
for immediate subordinates. A manager may award subordinates comp
time, subject to certain limits set in the system.
3. **Clerk:** A member of the HR department who has sufficient rights to view
employees’ personal data and is responsible for ensuring that employees’
information in all HR systems is up to date and correct. An HR clerk can
add or remove nearly any record in the system. In the real world, HR clerks
may or may not be employees; however, if they are employees, they use two
separate login IDs to manage these two different roles.
4. **System Admin:** A role responsible for the smooth running of the sys-
tem’s technical resources (e.g., Web server, database) and for collecting and
archiving all log files.

## Uses cases:
1. **Manage Time:** Describes how employees request and view vacation time
requests.
2. **Approve Request:** Describes how a manager responds to a subordi-
nate’s request for vacation time.
3. **Award Time:** Describes how a manager can award a subordinate extra
leave time (comp time).
4. **Edit Employee Record** Describes how an HR clerk edits an employee’s
information in the system. This includes setting all the leave time allow-
ances and the maximum time that can be awarded by the manager.
5. **Manage Locations:** Describes how an HR clerk manages location
records and their rules.
6. **Manage Leave Categories:** Describes how an HR clerk manages
leave categories and their rules.
7. **Override Leave Records:** Describes how an HR clerk may override
any rejection of leave time requests made by the rules in the system.
8. **Back Up System Logs:** Describes how the system administrator backs
up the system’s logs.
