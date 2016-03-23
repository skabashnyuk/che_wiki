Here are the notes of product meeting  February 23th, 2016.

#####TOPICS DISCUSSED:
1. Status on Codenvy OnPrem readiness for EclipseCon (pb on factories)
2. Review the goals for 4.0-GA
3. Discussion on Codenvy SaaS
4. Open Source Factories
5. Handling of issues between JIRA/GitHub
6. Next Sprint pre-planning
7. Internal use of Codenvy OnPrem on Azur

######ACTION ITEMS:
- Follow-up on GitHub/JIRA sync with Tasktop (Sergey with Dimitry)
- Create issue and figure out analytics requirements for 4.1 and Codenvy Saas Phase1 (Brad)
- Send email for pre-planning (Stévan)
- Create issues for default snapshots behaviours (Stévan)
- Communicate to community changes on VFS (Gennady + Vitalii)

######IMPORTANT POINTS ON TOPIC DISCUSSED:

**1. Status on Codenvy OnPrem readiness for EclipseCon**

Filter: https://jira.codenvycorp.com/issues/?jql=labels%20%3D%20eclipse-con16

We agreed to merge all needed features for EclipseCon by the end of the week, do a tagged release and stabilize its branch.
This way we don’t block the progress on master and we keep time to fix critical bugs that we may found over the upcoming week.


**2. Review the goals for 4.0-GA**

https://jira.codenvycorp.com/secure/Dashboard.jspa?selectPageId=16956

* **Continuous Development Workflow 1.0** done 
* **Codenvy on-prem hosted on Azure cloud**	done 	 
* **Workspace portability demo flow** done 
* **Microsoft VSTS devops flow use cases**

Coming along but the bottleneck is on the factories bug that we have on onprem.

* **Eclipse Initial Contribution**

Good spot. Code has been submitted and we'll be able to push our source code. IP need to check our source code. One CQ is remaining (for codemirror)	
In progress at Eclipse Foundation
1CQ to review 


* **Enhanced silky smooth loadings and transitions experience**

New animation has been designed. Currently in progress in Plugin team. Need by the end of this week. - 1/7 -

* **Add License key management in Codenvy onprem** Remaining has been pushed to 4.1
* **Change project creation flow**

2 bugs are remaining and needs to be fixed. They are planned in the current sprint - 50/52 -

* **Consoles panel** 

2 Bugs fixes remaining 	17/19

* **Images and Samples** done 


**3. Discussion on Codenvy SaaS**

Specification: https://docs.google.com/document/d/1syHjX2f2myWO6bwbzzhgjYiWy3dWjauN4NvwAeNKFrA/edit?ts=56c8ba94
And epic for phase 1: https://jira.codenvycorp.com/browse/CODENVY-134

Phase 1:
C4 will be a completely new installation.
We will export the accounts from C3 to C4 - but it’s not connected together. If account is changed in C3 it will not appear in C4, and vice-versa. 
NO migration of projects - we will only provide guidance to users.
4.1 is needed to run phase 1

Problems of analytics:
- the events have not been refreshed / cleaned
- maybe we could only dump the events in the database
Brad will create an issue to investigate what events are captured today and figure out what’s the minimum approach we could have.


**4. Open source factories**

Specification link: https://docs.google.com/document/d/1y3tOfPpWWhsfF5TLGhySb3X4cKCA4nVtfIpaCDmS9TY/edit

https://jira.codenvycorp.com/browse/CODENVY-135 added to the version 4.1

Factories are available inside of Che?
Acceptance of factory are done inside of a specific component in the IDE. This component is not part of Che

**5. Handling issues between jira/github**
Tasktop give us a licence of a tool which provide a way to sync issues between jira/github.
Dmitry has question about the installation of that plugin.
https://www.tasktop.com/integrations/github-sync

Apparently, the tool synchronize issues between jira/github, it also update comments and status of issues in booth way ( jira <-> github)

Separately, we will start publishing our roadmaps and weekly notes on GitHub.

**6. Next Sprint pre-planning**
For the upcoming sprint, the pre-planning email will be sent before the end of the current week.

**7. Internal use of Codenvy OnPrem on azur**
Sergey raised this topic.
Sergey tried in real-life and gave good feedback about the performances. 
Especially with the download of maven dependencies from central: they are retrieved nearly instantly so it’s really fast. Big difference in comparison of coding locally.

Sergey pointed that workspace snapshots are not handled by Dashboard. 
After discussion, it appears that restoring the state of the workspace as it has been leaved must be the default one:
existing workspace : auto-snapshot & auto-load snapshot
new workspace : always start from a base image

