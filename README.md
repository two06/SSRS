# SSRS Reports

Generic SSRS reports for pentesters, full details at https://www.secarma.co.uk/labs/ssrs-attacks-part-1-dynamic-data-extraction

## Getting Started

Upload the reports to a compromised SSRS server, modify the data source via the web interface and run.

### Show_DBs.rdl

This report allows you to view all tables (and their schemas) in a selected database. Use this report to find tables with interesting information, such as "Users".

### Table_Data.rdl

This report allows you to extract data from a specified table. Take the DB name, table name and table schema name from Show_DBs.rdl, supply the values to the report parameters and the table data will be dumped when the report is run. 

Data is separated by "-" characters. 



