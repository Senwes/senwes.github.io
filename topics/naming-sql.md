---
layout: site
title: SQL Standards and Naming Conventions
body_class: code
---

Make sure to read the [Handbook Extension: SQL](https://senwes.visualstudio.com/Applications/_wiki/wikis/Applications.wiki/22/Engineering-Handbook-Extension-SQL){:target="_blank"}.


* Datatype for datetime field should always be <b>DateTime2 </b> as recommended by Microsoft. [DateTime vs DateTime2 in Sql Server](https://www.tutorialsteacher.com/articles/datetime-vs-datetime2-in-sqlserver#:~:text=Microsoft%20recommends%20using%20DateTime2%20instead,Datetime2%20aligns%20with%20SQL%20standards){:target="_blank"}.
* Dates are always displayed as yyyy-MM-DD HH:mm or yyyy/MM/DD HH:mm in en-ZA format.

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
3.	Auto Incremented Primary keys are always named <i>Tablename</i>ID.
4.	Foreign key columns that have a relationship should be suffixed with _FK.
5.	Foreign keys should be named as follows <i>PKname</i>_FK.
6.	SQL Views are always prefixed with vw. 
