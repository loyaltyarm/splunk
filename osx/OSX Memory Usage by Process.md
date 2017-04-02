># macOS Memory Usage by Process 
-----

### Based on (scripts) data input configured from the [Splunk App for *Nix](https://splunkbase.splunk.com/app/273/)


```
sourcetype="YOURCUSTOMSOURCETYPEHERE" host="YOURINTENDEDHOSTHERE" | multikv fields RSZ_KB, COMMAND  | timechart eval(median(RSZ_KB)/1024) as ResidentMB by COMMAND
```

##### Notes:
- I have a custom time set for this search for the last hour (60 minutes), however you could view this in any timeframe.
- If the `sourcetype` or `host` name of your data input(s) is configured automatically (as here), you must change the `sourcetype` or `host` name to match your environment in order for this to work.
- Replace items in all CAPS with your value(s)