# Search based on Windows perfMon data for Disk Free Space from universal forwarder basic installation
# Sourcetype and data input configured automatically
# Free space value converted to inverse by subtracting from 100 as (original value is %)


sourcetype="Perfmon:Free Disk Space" host="YOURINTENDEDHOSTHERE" counter="% Free Space" Value="*" | eval Disk_Usage_% = 100 - Value | chart last(Disk_Usage_%)