> # Top PC Models 
-----

### Search syntax for the top deployed models with MDT below:
```
sourcetype="BDD" OR sourcetype="BDD-2" OR sourcetype="BDD-3" OR sourcetype="BDD-4"  AND "Property Model is now = " AND host="<yourintendedhosthere>" | dedup source | rex "\[Property Model is now = (?<PCMODEL>.*?)]" | top 100 PCMODEL
```

### Alternatively:

```
sourcetype="BDD*"  AND "Property Model is now = " AND host="YOURINTENDEDHOSTHERE" | dedup source | rex "\[Property Model is now = (?<PCMODEL>.*?)]" | top 100 PCMODEL
```

##### Notes:
- Based on Windows MDT Log data for BDD.LOG file specified in the `\DeploymentShare\Logs\*\BDD.LOG` location where * represents the directory created for each client imaged by MDT.
- MDT Log data from (BDD.LOG) is sometimes imported into Splunk into multiple BDD source types an issue that I am still investigating. For now, this search utilizes all of those source types, any source file, and specifies a host for restricting results to a specific server.