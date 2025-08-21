
2025-05-28

Tags:  [[ServiceNow]]
# Users and Personas
**Roles \[sys_user_role\]:** A role is functionally a key that allows a user to unlock a certain amount of access
## Admin Persona Types
- **System Administrators:** These people have very wide reaching power over the platform and have access to all platform features, applications, functions, and data
- **Specialized Administrators:** This role has System admin level powers, but only over specific functions or actions; Includes Assignment Rules, Knowledge Base, Human Resources, Reports, or Web Services.
- **Security Admin:** You should have very few of these, they are a buffed version of a System Admin

## User Persona Types
- **User/Requester \[sys_user\]:** A user is just an end user that can see knowledge Articles or create requests for themselves. Users can also be an application that needs service now access, so these programs can interface as a user. Users can also of course have multiple different roles in the platform.
- **Approver:** An Approver is someone who can approve requests but otherwise doesn't have much power in the system
- **Process Users:** They tend to work with It/process management for handling things like incidents

## Groups
**Users** are represented as a record in the User [sys_user] table, and they may: Update records, import data, request items, implement flows, approve knowledge content, run reports, and develop applications.

A **Group** is a collection of users, groups have a common purpose such as users approving change requests. 


**Groups\[sys_user_group\]:** Usually instead of assigning roles to users it makes more sense to give roles and permissions to groups of users, that way you can update the group as one and remove those permissions when they are removed from the group. Roles can also function as an object with inheritance but in reverse, the parent can do anything that its children can do

# References
[[Access Controls]]