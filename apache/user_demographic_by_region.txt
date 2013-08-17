# Search based on Apache access log data
# sourcetype should be set to access_* or access_combined when monitoring apache logs
# sourcetype not specified in this search as the only traffic for this host was apache access logs
# specify the sourcetype in order to further restrict data to specific apache access (or what works for your environment)

# this search must have Google Maps App for Splunk installed

# Apache Access User demographic by region

host="YOURINTENDEDWEBSERVERHOSTHERE" | geoip clientip | top limit=5 clientip_country_name