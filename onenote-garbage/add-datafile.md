# Add Datafile

```
Find Current datafiles on tablespace

select
substr(file_name,1,40) as File_Name,
substr(tablespace_name,1,10) as Tablespace_Name,
bytes/1024/1024 as Size_Mb
from dba_data_files
where tablespace_name = 'I_A_LARGE'
order by tablespace_name, file_name;


Add Datafile to tablespace

ALTER TABLESPACE I_A_LARGE ADD DATAFILE '+P30_DG1' SIZE 10G AUTOEXTEND ON NEXT 1G MAXSIZE 32767M;



See Tablespace info


select df.tablespace_name 'BOXITEMP',
       totalusedspace 'Used MB',
       (df.totalspace - tu.totalusedspace) 'Free MB',
       df.totalspace 'Total MB',
       round(100 * ( (df.totalspace - tu.totalusedspace)/ df.totalspace)) "Pct. Free"
  from (select tablespace_name,
               round(sum(bytes) / 1048576) TotalSpace
          from dba_data_files 
         group by tablespace_name) df,
       (select round(sum(bytes)/(1024*1024)) totalusedspace,
               tablespace_name
          from dba_segments 
         group by tablespace_name) tu
 where df.tablespace_name = tu.tablespace_name 
   and df.totalspace <> 0;

```

