# This search pulls the workflow used to image a machine with DeployStudio from each log in the DSS logs directory.
# Based on a (files and directories) data input configured as follows: /YOURDEPLOYSTUDIOREPO/Logs/*.log
#
#
# This data input as configured will not monitor the /Logs/Backup directory created by DSS during the imaging of multiple machines
# If the sourcetype of your data input is configured automatically or has any other name than "DSS Imaging Log" (as below), you must change that name in order for the search to work.

sourcetype="DSS Imaging Log" "Running workflow:" | rex "(?i)Running workflow: '(?P<WORKFLOWNAME>[^']+)" | top 100 WORKFLOWNAME