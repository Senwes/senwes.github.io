---
layout: site
title: SQL Standards and Naming Conventions
body_class: code
---

* Example for a naming a SQL table: HumanResources_PerformanceDevelopment_Approval
* Datatype for datetime field should always be <b>DateTime2 </b> as recommended by Microsoft. [DateTime vs DateTime2 in Sql Server](https://www.tutorialsteacher.com/articles/datetime-vs-datetime2-in-sqlserver#:~:text=Microsoft%20recommends%20using%20DateTime2%20instead,Datetime2%20aligns%20with%20SQL%20standards){:target="_blank"}.
* Dates are always displayed as yyyy-MM-DD HH:mm or yyyy/MM/DD HH:mm in en-ZA format.

### Encryption
* SQL Encryption is always used for data that can identify any entity/person in accordance with POPI act. 
* To query such a table a View will need to be created where the dbo.S_Decrypt method is called on the encrypted data. 
* varbinary(max) column is used for encrypted data.
* SenwesWebEncryption project/ Base 64 encryption can be used for data in transit.
* Mask POPIA sensitive columns: MASKED WITH (FUNCTION = 'partial(1, "xxxxx", 1)') .

### DB Structure<br />
<b>Senwes Applications employs a policy of business logic, does not reside in a DB but at the endpoint.</b>
1.	Entity Framework is the primary means of DB access through a repository pattern. 
	Stored Procedures alone will only be used for speed after it is determined that EF cannot handle the performance. As far as possible, the SP should be called from EF as well.
2.	Direct SQL queries should be used in certain conditions only. 
3.	As far as possible, SQL and Linq queries should be readable. Readability over ease of development/complexity.
4.	If a developer cannot understand or follow your code, the code is not readable. 
5.	We will only have one method that does one thing and one thing well so if a method already does an action, we will not re-code it.
6.	A method should do the basic action, and another should do a custom action if required. Example, 1 global method gets all employees and another will update those employees.

### Table Structures
1.  We always use word separators (underscore) to instead of spaces.
2.	Upper Camel Case table name convention is used (Aka Pascal Case).
	> Example: RequestStatus
3.	Auto Incremented Primary keys are always named <i>tablename</i>ID.
	> Example: RequestStatusID
4.	Foreign key columns that have a relationship should be suffixed with _FK.
5.	Foreign keys should be named as follows <i>pkname</i>_FK.
	> Example: RequestStatusID_FK
7.	All tables should always try to Implement the following columns: 
	> DateCreated, CreatedBy, CreatedByName, DateModified, ModifiedBy, ModifiedByName, IsRemoved
8.  OneID will be used to fill CreatedBy and ModifiedBy fields.
9.	OneID fields are always a varchar.
10.	EmployeeNo is always int.
11.	No relationship must be made FROM a table that constantly changes, SiteContactDetails or EmployeeDB. The reverse is allowed. 
12.	If you do not need to use varchar(max), 50 or 255 etc should be used instead.
13.	For SQL Encryption, varbinary(max) is used.
14.	SQL Views are always prefixed with vw. 
	> Example: vwEmployeeDB
