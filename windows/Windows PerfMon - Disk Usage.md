># Free Disk Space
---- 

### Search based on Windows `perfMon` data


```
sourcetype="Perfmon:Free Disk Space" host="YOURINTENDEDHOSTHERE" counter="% Free Space" Value="*" | eval Disk_Usage_% = 100 - Value | chart last(Disk_Usage_%)
```

##### Notes:
- Sourcetype and data input configured automatically
- Free space value converted to inverse by subtracting from 100 as (original value is %)
- Uses universal forwarder
- Replace value(s) in CAPS for your environment