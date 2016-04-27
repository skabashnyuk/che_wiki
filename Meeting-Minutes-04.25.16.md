Here are the notes of product meeting April 26th, 2016.

######TOPICS DISCUSSED:

1. Status of beta.codenvy.com 
2. Status of 4.2
3. SVN and contribution workflow to transition to Sergey's team
4. Status of 4.3
5. Review of Q2 Goals
6. General questions

######ACTION ITEMS:



#######IMPORTANT POINTS ON TOPICS DISCUSSED:


**1. Status of beta.codenvy.com**

beta.codenvy.com seems to get some stability issues.
We are working on those problems and adding tooling in order to be in better position to analyze the troubles.
Swarm seems to die, without we know the reasons. We are going to update the version of Swarm. 


**2. Status of 4.2**

4.2 Che and Codenvy: C++ and Python Stacks... 

We need to provide the debug commands for GDB associated with the C, C++, Python and Go stacks. We have not been able to work on that due to the work achieved for Artik IDE.

Next SHIP event will be on next wednesday and RELEASE will be on monday.
This give us more time to find a way to debug Python and Go.


**3. SVN and contribution workflow to transition to Sergey's team**

Setup a meeting with Stephane. for webhook on github. 

SVN plug-in will be activated and supported accordingly to the usual processes. 
SVN plug-in will have to be refreshed with the latest changes done on the ressources manager. 


**4. Status of 4.3**

We agreed to get a minimal scope on 4.3 with Maven Plug-in, Java Improvements and Permissions. 
As soon as 4.2 is released, feature branches for Maven and Permissions will be merged on master. 

Action: Document the API changes for the next release. (https://www.eclipse.org/eclipse/development/porting/4.4/incompatibilities.html)


**5. Review of Q2 Goals**



**6. General questions**
We discussed various topics coming from the community:
- how to support docker compose in workspace's environments
- versionning APIs
- graddle
- support of plug-in development with Eclipse IDE
- releases on Eclipse.org website