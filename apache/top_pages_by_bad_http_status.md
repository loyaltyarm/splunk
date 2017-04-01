># Apache Access Top Pages by bad HTTP status
-----

#### Search based on Apache access log data


```
host="YOURINTENDEDWEBSERVERHOSTHERE" status>300 | stats dc(clientip) as "unique ips" count as "total count" by uri, status
```

##### Notes: 
- `sourcetype` not specified in this search as the only traffic for this host was apache access logs
- specify the `sourcetype` in order to further restrict data to specific apache access (or what works for your environment)
- `sourcetype` should be set to `access_*` or `access_combined` when monitoring apache logs
- Replace items in all CAPS with your value(s)