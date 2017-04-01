# Search to pull Memory Usage Free vs. Used - Uses scripts from Splunk for *Nix application, all credit to its creators
# I generally run these for the past 3 hours, but you could look at any variety you like for a dashboard.
#
#
# If the sourcetype or host name of your data input(s) is configured automatically, you must change that name in order for the search to work.

sourcetype="<yourcustomsourcetype>" host="yourintendedhosthere" | multikv fields memFreePct, memUsedPct | timechart avg(memUsedPct) avg(memFreePct) | rename avg(memUsedPct) as "Used Mem", avg(memFreePct) as Free_Mem
