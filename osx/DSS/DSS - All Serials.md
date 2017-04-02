># All serial numbers in DeployStudio database
-----

### Based on a (files and directories) data input configured as follows: `/YOURDEPLOYSTUDIOREPO/Logs/*.log`


```
sourcetype="DSS Imaging Log" "Macintosh serial number:" | rex "Macintosh serial number: (?<MACSERIAL>.*)" | dedup MACSERIAL
```

##### Notes:
- This data input as configured will not monitor the /Logs/Backup directory created by DSS during the imaging of multiple machines
- If the `sourcetype` of your data input is configured automatically or has any other name than "DSS Imaging Log" (as here), you must change that name in order for the search to work.