># macOS Network Connections
-----

```
sourcetype="Apple Network Connections" host="YOURINTENDEDHOSTHERE" | head LIMIT=1 | multikv FIELDS ForeignAddress | rex FIELD=ForeignAddress "(?<hostOnly>^.*)[:\.].+$" | fields + hostOnly | where hostOnly != "*" | rename hostOnly AS Address | chart count BY Address | sort count DESC | rename count AS "# of Connections to This Address"
```

##### Notes:
- Based on a (files and directories) data input configured as follows: /YOURDEPLOYSTUDIOREPO/Logs/*.log
- This data input as configured will be *not* monitor the /Logs/Backup directory created by DSS during the imaging of multiple machines
- If the `sourcetype` of your data input is configured automatically or has any other name than "DSS Imaging Log" (as below), you must change that name in order for the search to work.
- Replace items in all CAPS with your value(s)