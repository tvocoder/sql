# sql

- To create:
``` mssql
CREATE PROCEDURE getAddress(@City VARCHAR(30))
AS
BEGIN
      SELECT * FROM Staff
      WHERE City = @City;
END;
GO
```

- To Execute:
``` mssql
EXEC getAddress @City = 'Houston';
```
