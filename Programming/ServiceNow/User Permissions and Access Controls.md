
[[ServiceNow]]

We can control access for [[Now; Users and Personas|users]] by using different types of roles. However, we can't just control what people can see in the UI, we need to have a database access layer so that people can't just click hyperlinks.

If we want to change the security part of it we need to elevate our permission to a security admin, which functions like sudo and is session specific.

What is important to remember is that if we take a table with no access rules, which means everything is unlocked by default, and then we put a rule on it. Then we restrict access for everyone who wasn't explicitly given it.

**Access Controls**
an access control is a security rule defined to restrict a user from viewing data, and using service now specific and [[CRUD]] operations. It is executed when attempting to access any ServiceNow table and may be set at the row level or at the column level. 

We can change the access controls in the **Access Control List (ACL)** which controls the instances access control rules. We also inherit some roles by default (one for each in [[CRUD]]).

Each access control specifies a valid operation, the object being secured, and the permissions required to access the object. We can also introduce context specific permissions as well, say the person who created the form can update it.

Wildcards are important since they function as a skeleton key
house.none (front door) for both Maurice and Larry
house.* for Maurice, all internal doors are now closed and locked and Maurice can access them all
house.room2 for Larry. The result is that Maurice sees everything but room 2 and Larry sees room 2.

![[Pasted image 20241208145952.png]]


# References:
[[Access Controls]]