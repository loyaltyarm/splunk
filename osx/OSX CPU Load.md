># macOS % CPU Load
-----

### - Based on (scripts) data input configured from the [Splunk App for *Nix](https://splunkbase.splunk.com/app/273/) (included cpu.sh script)


```
sourcetype="Apple CPU" host="YOURINTENDEDHOST" | multikv fields pctIdle | eval Percent_CPU_Load = 100 - pctIdle | timechart avg(Percent_CPU_Load) by host
```

##### Notes:
- I moved these scripts from the [Splunk App for *Nix](https://splunkbase.splunk.com/app/273/) in order to maintain a single app (search) dashboard for manager reporting
- You will need to set the `sourcetype` and `host` to fit your environment. Alternatively to this search, you can use the [Splunk App for *Nix](https://splunkbase.splunk.com/app/273/) which is in many cases a better alternative.
- Replace items in all CAPS with your value(s)