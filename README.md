# SSRS Reports

Generic SSRS reports for pentesters, full details at https://www.secarma.co.uk/labs/ssrs-attacks-part-1-dynamic-data-extraction and https://www.secarma.co.uk/labs/ssrs-attacks-part-2-building-an-empire

Currently, only SQL Server 2016 is supported. The blog posts should contain enough information to allow you to build these reports for older versions. 

## Getting Started

Upload the reports to a compromised SSRS server, modify the data source via the web interface and run.

### Show_DBs.rdl

This report allows you to view all tables (and their schemas) in a selected database. Use this report to find tables with interesting information, such as "Users".

### Table_Data.rdl

This report allows you to extract data from a specified table. Take the DB name, table name and table schema name from Show_DBs.rdl, supply the values to the report parameters and the table data will be dumped when the report is run. 

Data is separated by "-" characters. 

### Check_Privs.rdl

This report shows if xp_cmdshell is enabled, if the data source user is a member of the sysadmin group and the username that the data source is connecting as.

### Enable_xp_cmdshell.rdl

This report will attempt to enable xp_cmdshell. The indicator will update once the report is refreshed. You can also re-run Check_Privs.rdl to confirm the change. 

### run_command.rdl

Allows arbitrary commands to be passed to xp_cmdshell. There is a 2000 char limit on the command parameter, the report will display an error if your payload exceeds this limit. Check the blog posts for example payloads. 

### dirtree.rdl

Runs xp_dirtree against a user supplied path. The intention is to allow you to capture NTLM hashes by providing a UNC path pointing to Responder, but this will also display a simple directory listing if a local path is used. 

To capture hashes, you must run a tool like responder, see the blog posts for examples. 
