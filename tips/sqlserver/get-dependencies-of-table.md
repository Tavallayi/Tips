# Get dependencies of table

Method 1: Using DMV ```sys.dm_sql_referencing_entities```

```sql
 SELECT referencing_schema_name, referencing_entity_name,
 referencing_id, referencing_class_desc, is_caller_dependent
 FROM sys.dm_sql_referencing_entities ('dbo.First', 'OBJECT');
 GO
```

Method 2: Using ```information_schema.routines```

```sql
 SELECT *
 FROM information_schema.routines ISR
 WHERE CHARINDEX('First', ISR.ROUTINE_DEFINITION) > 0
 GO
```

Method 3: Using ```sp_depends```

```sql
 exec sp_depends 'dbo.First'
 GO
```

# Thanks: 
* [Mala](https://stackoverflow.com/users/3296844/maMala) for your [answer](https://stackoverflow.com/a/22005907)