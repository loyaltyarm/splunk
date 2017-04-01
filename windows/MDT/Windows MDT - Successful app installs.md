# Search based on Windows MDT Log data for BDD.LOG file specified in the \DeploymentShare\Logs\*\BDD.LOG location, 
# where * represents the directory created for each client imaged by MDT.

# MDT Log data from (BDD.LOG) is sometimes imported into Splunk into multiple BDD source types, 
# an issue that I am still investigating. For now, this search utilizes all of those source types, 
# any source file, and specifies a host for restricting results to a specific server.
#
# 
# Free space value converted to inverse by subtracting from 100 as (original value is %)


sourcetype="BDD" OR sourcetype="BDD-2" OR sourcetype="BDD-3" OR sourcetype="BDD-4" AND host="YOURINTENDEDHOSTHERE" AND "Application * installed successfully" | rex "Application (?<PCAPP>.*) (?=installed successfully)" | top 100 PCAPP | dedup PCAPP