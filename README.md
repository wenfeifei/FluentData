News
March 2015: Version 3.0.1 is released on CodePlex and NuGuet, and a version 4 is currently in the pipeline. Sybase supported has been added, see the documentation tab for more information.
December 30th: Version 3.0 is released on CodePlex and NuGet. The documentation has been updated.
August 8th: Version 2.3 is released on CodePlex and NuGet. This release is available both as an assembly file and as a single source code file. PostgreSQL, SQLite and IBM DB2 are now supported. A select builder with paging support has been added. The documentation will soon be updated with more information on the new features.
June 3rd: Version 2.2.2 is released.
May 8th: Version 2.2 is released.
April 15th: Version 2.1 is out with support for MS Access.
Mar 12th: Version 2.0 is now out on CodePlex and NuGet.
Mar 3rd: FluentData is now available on NuGet.
Feb 28th: Version 1.2 of FluentData is out with support for QueryValues and automapping to enumerations.
Feb 19th: Version 1.1 of FluentData is out with support for MySQL.
Feb 14th: The first version (1.0) of FluentData is out on CodePlex.
Roadmap
Click here to view the backlog.
About
Are you tired of fighting with overly complex ORMs such as Entity Framework and NHibernate? Are you tired of poorly generated SQL or having to change your business objects to work with your ORM? Do you miss the power and performance of ADO.NET and SQL, but not the manual tedious work? If so FluentData might be the framework for you.

FluentData is a Micro ORM that makes it simple to select, insert, update and delete data in a database. It gives the developer the power of ADO.NET but with the convenience of an ORM. It has a simple to use fluent API that uses SQL - the best and most suitable language to query data, and SQL or fluent builders to insert, update and delete data.
Features
Basic features
Supports the following databases
MS SQL Server
MS SQL Server Compact 4.0
MS SQL Azure
MS Access
Oracle
MySQL
SQLite
PostgreSQL
IBM DB2
Sybase
Use SQL to select data, and SQL or fluent builders to insert, update and delete data.
Supports stored procedures.
Supports paging.
Queries are auto mapped or custom mapped to your own entity type (such as a Product type) or to a dynamic type (new in .NET 4.0).
Secure, use indexed or named parameters to prevent SQL injection.
Great performance.
Can work against any existing business objects and the business layer do not need any references to FluentData.
Available both as an assembly (.DLL) and as a single source code file.
Advanced features
Transactions
Multiple result set - Execute multiple queries as a single database hit for improved performance.
Custom return collections, e.g. ProductCollection instead of List<Product>.
Supports creation of complex entity objects through a custom Entity Factory.
Provider model that makes it easy to add support for other databases.
Contributions
Fluency (Code Generation Templates)
Getting started
FluentData is easy to use,and more useful description,see the document here:
