# Search to pull CPU idle info and convert to Load by subtracting pctIdle from 100.
# Based on a (scripts) data input configured from the Splunk App for *Nix (included cpu.sh script)
# I moved these scripts from the Splunk App for *Nix in order to maintain a single app (search) dashboard at the request of my manager
#
#
# You will need to set the sourcetype and host to fit your environment. Alternatively to this search, you can use the Splunk App for *Nix which is in many cases a better alternative.

sourcetype="Apple CPU" host="YOURINTENDEDHOST" | multikv fields pctIdle | eval Percent_CPU_Load = 100 - pctIdle | timechart avg(Percent_CPU_Load) by host