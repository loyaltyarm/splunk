># Apache Access Top User Agent
-----

### Search based on Apache access log data

```
host="YOURINTENDEDWEBSERVERHOSTHERE" | top limit=10 useragent
```

##### Notes:
- `sourcetype` should be set to `access_*` or `access_combined` when monitoring apache logs
- `sourcetype` not specified in this search as the only traffic for this host was apache access logs
- specify the `sourcetype` in order to further restrict data to specific apache access (or what works for your environment)
- Replace items in all CAPS with your value(s)