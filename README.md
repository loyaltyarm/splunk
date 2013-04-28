>splunk
======

Collection of Splunk searches for monitoring Windows and OS X systems. Some are adapted from the Splunk Apps for Windows and Unix, credit for base scripts and statistics is owed to the creators of those splunk applications. These are strictly search syntaxes being posted for community usage.

#Environment architecture info
My splunk environment resides on an OS X server running 10.8.x. (Its primary function is as a DeployStudio master) Universal forwarders are installed on Windows systems (MDT environment servers) and forward performance data to the OS X server. In the current environment, universal forwarder data is also being forwarded from a redundant OS X server running 10.8.x that serves as a DeployStudio slave.

#Reporting information
Currently, I am building a performance monitoring environment for MDT and DeployStudio from the setup above. The DeployStudio environment is not as widely used in our enterprise as the MDT system, however because Splunk resides on the DSS master, I am pulling local reporting from the DSS logs on most common Apple model, top image workflow, and Average restore, task, and install times from each workflow.

With regards to the MDT environment, I will only pull perfMon information from the MDT systems individually until I am able to gauge the amount of data used versus the Splunk daily limit.

#Acknowledgements
http://nbalonso.com/the-logs-talk/

#Contact
These searches may not work as advertised in your environment. If you are attempting to report on specific data, or have a correction or addition, feel free to let me know via loyaltyarm@gmail.com.
