##TOPICS DISCUSSED:

​1. 5.0.0-M4 status  
2. 5.0.0-M5 status  
3. Remove che-in-che stack for saas + onprem  
4. NPM issues reported by stevan?  
5. Any LS bugs remaining? #2614  
6. Change docs version from 5.0.0-M3 to just 5.0  
7. Port routing.  


##IMPORTANT POINTS ON TOPICS DISCUSSED:

####​1. 5.0.0-M4 status 
Hotfix release for 5.0.0-M3. Will be done ASAP. Most likely in the next couple of days.

####2. 5.0.0-M5 status  
Will be done before the end of this spring. Dependent on LDAP integration. Issues not done when LDAP is completed will be pushed to 5.0.0-M6.

####3. Remove che-in-che stack for saas + onprem  
Added to M5 release.

####4. NPM issues? #2608
Moved to next sprint. Will be fixed next-sprint by workaround and possibly #1944 . 

####5. Any LS bugs remaining? #2614
No blockers. Adding to M5 for Codenvy.

####6.Change docs version from 5.0.0-M3 to just 5.0.0 
This will happen.

####7.Port routing.
Codenvy uses 444 because Che uses 443. Investigating:
1. See if Codenvy and Che can both use 443 at the same time.  
2. Looking at using only one port for all traffic by putting HAProxy in front of Nginx for port 443/444.   
3. Replace HAProxy with Nginx or vice versa.  
4. Remove ephemeral ports.  

A meeting has been setup to discuss this idea further.