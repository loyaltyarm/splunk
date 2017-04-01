# Search to pull Memory Usage by Process - Uses scripts from Splunk for *Nix application, all credit to its creators
# I have a custom time set for this search for the last hour (60 minutes), however you could view this in any timeframe.
#
#
# If the sourcetype or host name of your data input(s) is configured automatically (as below), you must change the sourcetype or host name to match your environment in order for this to work.

sourcetype="<yourcustomsourcetypehere>" host="<yourintendedhosthere>" | multikv fields RSZ_KB, COMMAND  | timechart eval(median(RSZ_KB)/1024) as ResidentMB by COMMAND
