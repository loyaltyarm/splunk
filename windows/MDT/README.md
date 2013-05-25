>splunk for MDT
======

# Setup and Initial Thoughts
For my MDT data, I wanted to continue to work to gauge the daily amount of data being catalogued by the Splunk master, as I am still testing on a free plan (must be under 500mb daily traffic). For the purposes of my MDT deployment log tests, I am only forwarding the BDD.LOG file to the Splunk server to searching. This is for several reasons, but capturing the number of logs on an MDT system for each deployed client can be especially painful to the daily total if your MDT deployment server is highly utilized like in my environment.

So, on your test MDT system, install the Windows universal forwarder from splunk. Be sure to grab the one for your architecture, 32 vs. 64. During install, point the universal forwarder to your receiving server's hostname and port, the default suggestion being 9997 for receiving on the splunk master. After doing so, check the boxes applicable to your monitoring needs, however be sure to note that AD logging, as well as Windows event logging takes up a lot of space. For the purposes of my thoughts here, I only enabled perfMon and selected the \\DeploymentShare\Logs\ directory for monitoring. Now once the installer is finished, your master splunk server will get a huge spike from incoming data from that box. Go ahead and close the installer, and navigate into the services manager and disable the Splunk forwarding service by stopping it, for now.

# Whitelisting
We need to whitelist the BDD.LOG file, as well as modify the directory that we wish to monitor. I will describe what has worked for me in my tests. After stopping the service, navigate to Program Files>SplunkUniversalForwarder>etc>apps>MSIcreated>local>inputs.conf and open that with a text editor (Notepad will work fine). In this file you should see all of your perfMons listed, as well as any others you enabled during the install. We will edit the entry and add the whitelist line as shown below:

[monitor://C:\DeploymentShare\Logs]
whitelist = \BDD.LOG$
disabled = false

After saving the change and exiting, go into the services manager of your MDT box and 'start' the service again. This should begin indexing only the BDD data from your server's client deployment logs. Since MDT creates a folder for each individual client, the whitelist allows you to upload only the BDD.LOG from each folder in the directory specified for monitoring. If any other sourcetypes appear in your splunk sourcetypes list, you may need to investigate further changes. You can also feel free to contact me at loyaltyarm@gmail.com to see if I can assist. Again, this is what has worked for me, use in your testing and see what has worked for you.

# Searches
The searches are based on information contained in the BDD.LOG, and are based on both my management's need for specialized reporting on those variables, as well as my own curiosity to see what could be reported on. I hope you find them enjoyable and useful.
