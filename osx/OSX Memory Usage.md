># macOS Memory Usage Free vs. Used
-----

### Based on (scripts) data input configured from the [Splunk App for *Nix](https://splunkbase.splunk.com/app/273/)

```
sourcetype="YOURCUSTOMSOURCETYPE" host="YOURINTENDEDHOSTHERE" | multikv fields memFreePct, memUsedPct | timechart avg(memUsedPct) avg(memFreePct) | rename avg(memUsedPct) as "Used Mem", avg(memFreePct) as Free_Mem
```

##### Notes:
- I generally run these for the past 3 hours, but you could look at any variety you like for a dashboard.
- If the `sourcetype` or `host` name of your data input(s) is configured automatically, you must change that name in order for the search to work.
