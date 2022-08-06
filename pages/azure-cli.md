

```
az configure --defaults group=[sandbox resource group name] sql-server=[server-name]
az sql db list
az sql db list | jq '[.[] | {name: .name}]'
az sql db show --name [Database Name]
az sql db show --name [Database Name] | jq '{name: .name, maxSizeBytes: .maxSizeBytes, status: .status}'
```




---


Displaying connection string:

```
az sql db show-connection-string --client sqlcmd --name [Database Name]
```

Output:

```
"sqlcmd -S tcp:contoso-1.database.windows.net,1433 -d [Database Name] -U <username> -P <password> -N -l 30"
```

Note: when writing username and password, use `'` single quote so that there is no problem between the string and the substring.




When you write that string in bash, you will be able to execute SQL commands.


```
sqlcmd -S tcp:contoso-1.database.windows.net,1433 -d [Database Name] -U <username> -P <password> -N -l 30
    CREATE TABLE Drivers (DriverID int, LastName varchar(255), FirstName varchar(255), OriginCity varchar(255));
    GO
    SELECT name FROM sys.tables;
    GO

```























