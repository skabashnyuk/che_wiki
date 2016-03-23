Here are the notes of product meeting February 16th, 2016.

######TOPICS DISCUSSED:
1. Explanation on new website
2. Beta of Codenvy
3. Che issues to migrate to GitHub issues
4. Release Plan March1
5. Q2 Objectives 
6. Review the goals for 4.0-GA
7. Other topics:
     - onpremises + cloudide assemblies


#####ACTION ITEMS:
- Move forward on backlogs consolidations for Codenvy and Che (Stévan)
- Detail requirements for epic on VFS https://jira.codenvycorp.com/browse/IDEX-4055 (Gennady)
- Add BV on missing issues (Collective Ownership)
- Figure out a solution for Github Issues / JIRA (Collective Ownership)
- Start conversation to provide information about how many user can be added to codenvy beta (Roman)
- Discuss the technology issues and cleanup the backlog (Stevan/Gennady)
- First draft requirements for Q2 objectives for mid-march (Collective Ownership)
- Plan discussions about risks/actions on Codenvy on Codenvy goals for Q1 (Stevan)

######IMPORTANT POINTS ON TOPIC DISCUSSED:

**1. Explanations on new codenvy.com website**

A new website is live. 2 majors changes:
- Welcome to an all-new Codenvy : explanation about better agile method
- New Getting started. Choose between OnPrem / Saas

Wednesday, email to our user database for Codenvy Beta. Codenvy beta is done on beta.codenvy.io on Azure

**2. Beta of Codenvy**

Discussions occurred around how do we know how many users we can have concurrently on the server.
- Roman + Sergey + Tyler will discuss about the metrics, the stability to know how many users can be added. 
- When limit reached, we will add new node to provide more ressources.
- Marketing will pick-off some name from the queue each days, based on info provided by sys-ops.

We might have problems with workspaces as we don’t really know if the workspace is active or not and when we could shutdown them. A proposal could be to force shutdown the workspaces each days. 
@Roman: to start conversation on slack on this topic

**3. Che Issues to migrate to GitHub**

Questions have been asked around how to export the issues from JIRA to GitHub and what are the policies.
- Should we clone issues to github only? vice-versa?
- Only issues for che on github.com/che

Team is not really convinced that we should stop using JIRA for Che as it will complexify the management of sprint.
Tyler would like to assume that github is the record of truth as it is the only place where the community can collaborate. JIRA should act as a slave of github.

Timeframe: All issues in CHE must be exposed to community on GitHub before March 1. 
To do that "Collective Product Owners" must decide and define the rules
Nobody has been declared to lead this topic. 

**4. Release plan for March 1**

Backlog clearing… 
All issues in the backlog must have a BV.
A new release needs to occur as another milestone to GA for March1.

**5. Review Q2 Objectives**

We reviewed the Q2 Objectives.

1st Draft specs for middle-march. 
Gennady request to define some dates to discuss the specs then.

Every "owners" must start to think and discuss about the goals and the ideas get on them by initiating email thread. 

**6. Review the goals for 4.0-GA**

* **Continuous Development Workflow 1.0**

Almost completed. Moving of plugin-git and plugin-jira is supposed to be completed before end of sprint.. General Oauth/SSH will be fixed by the work on the microsoft use case.	19/22

* **Codenvy on-prem hosted on Azure cloud**

Scalability will not be handled for the time being.	

* **Workspace portability demo flow**

First demoflow is ready, but need polish. This epic is done.

* **Microsoft VSTS devops flow use cases**

Oauth troubles are solved.

* **Codenvy on Codenvy**

Docker in Docker is not working and not acceptable solution. In hosted version it is unsecure. Vitalii and Gennady had some thinking about that. Just initial discussion. There is no action on this epic and it needs to be discussed separately. At this moment, this epic is not going to be handled.	0/6

* **Eclipse Initial Contribution**

Good spot. Code has been submitted and source code pushed to eclipse repo.	In progress at Eclipse Foundation

* **Add user management to on-prem**

Improvements on API planned for next sprint, so we will have initial set of features done.

* **Enhanced silky smooth loadings and transitions experience**

Factory loading experienced has been discussed; New animation is in progress. Stevan will draft a flow so that we can agreed on how to handle the user experience. For the time being, it appears that loading sequence will be needed in dashboard and in IDE.	0/3

* **Replace VFS implementation including configurable FS watchers with callbacks**

First step of the work is in progress. Some success on Server / Next sprint some other parts of the server side. But more code depends on that on client. Not in time for March 1 / Good for Q1.	Gennady will detail more the requirements

* **Add License key management in Codenvy onprem**

Remaining work only for UD. Should be completed by the end of the sprint

* **Change project creation flow**

Few bugs are remaining and needs to be fixed. Roman raised a problem with websocket, he'll create the appropriated issues so we can track those issues

* **Support Packages**

Anatoliy and Eugene will start detailling the requirements.	

* **Consoles panel**

This work is going a bit slowly. Stevan will trim the requirements so we can get this epic completed for GA - then plan improvements.

* **Images and Samples**

PR to provided Stacks management from server side is in review.	


**7. Other topics**

- cloud-ide assembly will be remove for the time being from 4.x