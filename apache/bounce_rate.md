># Apache Access Bounce Rate
-----

### Search based on Apache access log data

```
sourcetype="access_*" | transaction clientip maxpause=1h keepevicted=t mvlist=t | eval user_type=case(eventcount=1, "Bounced", eventcount<=5, "2-5 pages", eventcount<=10, "6-10 pages") | top limit=5000 user_type
```
##### Note:
>`sourcetype` should be set to `access_` or `access_combined` when monitoring apache logs