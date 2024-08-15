# Reorganize-indexes-in-Smartstore-DB
Reorganize indexes in Smartstore DB tables

## Reorganize
Use REORGANIZE for slightly fragmented indexes.

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
