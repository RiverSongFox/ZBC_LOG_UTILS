ZBC_LOG_UTILS
=============

As SAP Link doesn't support Enhancements, you should create one manually after installation of the Nugget. Open function module `BAL_DB_DELETE` and create Implicit Enhancement at the end of the FM:

```
  DATA S_I_T_LOGS_TO_DELETE LIKE LINE OF I_T_LOGS_TO_DELETE.
  LOOP AT I_T_LOGS_TO_DELETE INTO S_I_T_LOGS_TO_DELETE.
    DELETE FROM ZBC_LOG_DATA
      WHERE LOG_HANDLE = S_I_T_LOGS_TO_DELETE-LOG_HANDLE.
  ENDLOOP.
  COMMIT WORK.
```

This will enable deletion of Details data for log entries.
