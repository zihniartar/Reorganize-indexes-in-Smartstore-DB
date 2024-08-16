# Reorganize-indexes-in-Smartstore-DB
Reorganize indexes in Smartstore DB tables

## Reorganize
Use REORGANIZE for slightly fragmented indexes.
Die REORGANIZE-Option defragmentiert den Index auf Seitenebene und ist eine weniger aufwendige Operation im Vergleich zum Neuaufbau des Indexes. Diese Methode wird in der Regel verwendet, wenn der Fragmentierungsgrad des Indexes gering ist (zum Beispiel unter 30%).

### Reorganize Indexes in Customer table
```bash
ALTER INDEX [IX_Deleted] ON [Customer] REORGANIZE;
ALTER INDEX [IX_SystemName] ON [Customer] REORGANIZE;
ALTER INDEX [IX_Customer_LastIpAddress] ON [Customer] REORGANIZE;
ALTER INDEX [IX_Customer_CreatedOn] ON [Customer] REORGANIZE;
ALTER INDEX [IX_Customer_LastActivity] ON [Customer] REORGANIZE;
ALTER INDEX [IX_BillingAddress_Id] ON [Customer] REORGANIZE;
ALTER INDEX [IX_ShippingAddress_Id] ON [Customer] REORGANIZE;
ALTER INDEX [IX_Customer_Email] ON [Customer] REORGANIZE;
ALTER INDEX [IX_Customer_Username] ON [Customer] REORGANIZE;
ALTER INDEX [IX_Customer_CustomerGuid] ON [Customer] REORGANIZE;
ALTER INDEX [IX_Customer_FullName] ON [Customer] REORGANIZE;
ALTER INDEX [IX_Customer_Company] ON [Customer] REORGANIZE;
ALTER INDEX [IX_Customer_CustomerNumber] ON [Customer] REORGANIZE;
ALTER INDEX [IX_Customer_BirthDate] ON [Customer] REORGANIZE;
ALTER INDEX [IX_Customer_Deleted_IsSystemAccount] ON [Customer] REORGANIZE;
ALTER INDEX [IX_IsSystemAccount] ON [Customer] REORGANIZE;
```

### Reorganize Indexes in GenericAttribute table
```bash
ALTER INDEX [IX_GenericAttribute_Key] ON [GenericAttribute] REORGANIZE;
ALTER INDEX [IX_GenericAttribute_EntityId_and_KeyGroup] ON [GenericAttribute] REORGANIZE;
```

## Rebuild
Use REBUILD for heavily fragmented indexes.
The REBUILD option completely rebuilds the index and is the preferred method if the fragmentation level is high (e.g. over 30%). This is a more resource-intensive operation, but offers a more comprehensive optimization of the index.

### Rebuild Indexes in Customer table
```bash
ALTER INDEX [IX_Deleted] ON [Customer] REBUILD;
ALTER INDEX [IX_SystemName] ON [Customer] REBUILD;
ALTER INDEX [IX_Customer_LastIpAddress] ON [Customer] REBUILD;
ALTER INDEX [IX_Customer_CreatedOn] ON [Customer] REBUILD;
ALTER INDEX [IX_Customer_LastActivity] ON [Customer] REBUILD;
ALTER INDEX [IX_BillingAddress_Id] ON [Customer] REBUILD;
ALTER INDEX [IX_ShippingAddress_Id] ON [Customer] REBUILD;
ALTER INDEX [IX_Customer_Email] ON [Customer] REBUILD;
ALTER INDEX [IX_Customer_Username] ON [Customer] REBUILD;
ALTER INDEX [IX_Customer_CustomerGuid] ON [Customer] REBUILD;
ALTER INDEX [IX_Customer_FullName] ON [Customer] REBUILD;
ALTER INDEX [IX_Customer_Company] ON [Customer] REBUILD;
ALTER INDEX [IX_Customer_CustomerNumber] ON [Customer] REBUILD;
ALTER INDEX [IX_Customer_BirthDate] ON [Customer] REBUILD;
ALTER INDEX [IX_Customer_Deleted_IsSystemAccount] ON [Customer] REBUILD;
ALTER INDEX [IX_IsSystemAccount] ON [Customer] REBUILD;
```





### Rebuild Indexes in GenericAttribute table
```bash
ALTER INDEX [IX_GenericAttribute_Key] ON [GenericAttribute] REBUILD;
ALTER INDEX [IX_GenericAttribute_EntityId_and_KeyGroup] ON [GenericAttribute] REBUILD;
```

## Reorganize all indexes of a table
```bash
ALTER INDEX ALL ON [TableName] REORGANIZE;
```

## Rebuild all indexes of a table
```bash
ALTER INDEX ALL ON [TableName] REBUILD;
```



# Check degree of fragmentation


```bash
SELECT
    a.index_id,
    name,
    avg_fragmentation_in_percent
FROM
    sys.dm_db_index_physical_stats(DB_ID(), OBJECT_ID('TableName'), NULL, NULL, 'LIMITED') AS a
JOIN
    sys.indexes AS b ON a.object_id = b.object_id AND a.index_id = b.index_id
WHERE
    avg_fragmentation_in_percent > 10;

```


# List all table names in a database
```bash
SELECT TABLE_NAME
FROM INFORMATION_SCHEMA.TABLES
WHERE TABLE_TYPE = 'BASE TABLE'
ORDER BY TABLE_NAME;

```
