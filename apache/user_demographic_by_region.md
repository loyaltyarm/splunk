># Apache Access User demographic by region
-----

### Search based on Apache access log data

```
host="YOURINTENDEDWEBSERVERHOSTHERE" | geoip clientip | top limit=5 clientip_country_name
```

##### Notes:
- `sourcetype` should be set to `access_*` or `access_combined` when monitoring apache logs
- `sourcetype` not specified in this search as the only traffic for this host was apache access logs
- specify the `sourcetype` in order to further restrict data to specific apache access (or what works for your environment)
- this search must have [Google Maps App for Splunk](https://splunkbase.splunk.com/app/368/) installed
- Replace items in all CAPS with your value(s)

