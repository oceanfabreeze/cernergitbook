# Skip Readme

```
update into dm_ocd_log dol 
set dol.status = "SUCCESS", 
dol.message = "Readme Manually Marked as Auto-Success" 
where dol.environment_id = (select di.info_number 
from dm_info di where di.info_domain = "DATA MANAGEMENT" 
and di.info_name = "DM_ENV_ID") 
and dol.project_type = "README" 
and dol.project_name = "11130" 
and dol.status = "FAILED" go
```

