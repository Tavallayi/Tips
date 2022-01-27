
```sql
select left(name, charindex('_',name)-1) 
from tempdb..sysobjects
where charindex('_',name) > 0 and
xtype = 'u' and not object_id('tempdb..'+name) is null
```


https://stackoverflow.com/a/7075585

20220117
