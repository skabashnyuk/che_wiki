# PARTICIPANTS:

- Gennady Azarenkov
- Florent Benoit
- Gorkem Erkan
- Roman Iuvshyn
- Eugene Ivantsov
- Alexander Garagatyi
- Stevan LeMeur
- Mario Loriedo
- Vitalii Parfonov
- Anna Shumilova

# TOPICS DISCUSSED:

1. Release of 5.15.0
2. Remaining work on new workspace details pages
3. Next sprint plans?
4. Strat work on Command Palette https://github.com/eclipse/che/issues/4993
6. Freesia train planning objectives - results of Dev BU management meeting last week
7. Codenvy customer support and business plan
8. Review the development process document
9. Multi-tenant Che on OSIO
10. Build centos-based image of Che server
11. Brno face to face agenda ([doc](https://docs.google.com/document/d/1Tw6BWm-4Qji_MzgnZmQejA4nrepdrWJQrBEqDDdNaWQ/edit#))
12. Call for papers from EclipseCon Europe 2017


# DETAILED MINUTE:

TOPICS FOR DISCUSSING:

### Release of 5.15.0 on tuesday
4 open issues, any blockers. Looks like we are ready for release 5.15

### What’s the remaining work on new workspace details pages? If we do 5.16, can we add that into? 
Ann propose move to 5.17

### Next sprint plans? 
Propose for sprint are ready. Tomorrow (18/07/2017) will be estimate meetings
  
### IDE - Start of work on Command Palette
 IDE team will start work on it. It will be POC. Issue is to big for one sprint.

### Freesia train planning objectives - results of Dev BU management meeting last week:
* **Core Objective**: Ship Che 6 w/ SPI, OpenShift, keycloak, IDE re-design, workspace loading
* **Core Objective**: Dogfooding objectives … various IDE improvements to support dogfooding
* **Core Objective**: Complete specification (and maybe reference implementation) of JavaScript API for plugins (moving Florent’s investigations into a full markdown specification with various APIs and samples that can be shared with community for discussion and also presented at CheConf 2017)

* **Stretch Objective**: improvements to IDE for Try It Now experience.  I started this thread with Stevan, but needs thought + investigation.  Basic idea is whether we can improve how new users to a technology learn that technology by re-configuring the views of the IDE when an action is executed - change the project tree, which files are open, which lines are highlighted, and which panel / popup is displayed (with HTML help)
* **Stretch Objective**: exploration to have Che bundled within the DevSuite / CDK bundle that is shipped by RHT. There are not a lot of thinking on this yet, but RHT’s standard bundle is installing their own Docker daemon, configuring it, and the thinking is why not have Che installed and running as well?

_* Core Objective - clear for team_
_* Stretch Objective - any comments for now_


### Codenvy customer support and business plan - see notes from email;

Brad can walk through specifics and offer any Q&A. There is no action item here - just a discussion so that everyone is on the same page.

Current Codenvy customer support:
Proposal: Support Codenvy 5 for at least one more renewal cycle. When Che 6 / OSIO are good enough to support enterprise teams, we will work with each customer to move them to Che 6 / OSIO.
Eugene commented that it will be very hard to move customers to Che 6 or OSIO, it’s basically a reinstall and re-implement. For customers like TIAA this could be a long process.
Brad replied that we need the long support timeline for this reason and that we won’t start looking at moving customers until Jan 2018 at the earliest.
 
           
### Review the development process document. 
Have we concluded the analysis of maintainers?  Is the language in the dev process document finalized?  If not finalized, we need another review cycle and then once finished, update the wiki.

Looks like we done this task. Roman add special command pr-test for testing PR on our CI.
Core concepts are complete. Needs another top-to-bottom review of language before posting by PM.

### KC support is a pre-req for multi-tenant Che on OSIO. Do we have an idea about when this will be available? Are there any risk?

Sergii will have more info end of this week. Will organize meeting for agreement status  

### Build centos-based image of che server too (e.g. eclipse/che-server:centos-nightly)?
Mario will create issue for Roman for this task

### Brno face to face agenda (doc link)
Team will review add comment and discus next few weeks

### Source code license for Che and Codenvy?
Sergii will send mail with description of problem 

### Support for OSIO Che

Che 6 needs to be able to run on OSIO. Needs to be added to Freesia goals.

### Call for papers from EclipseCon Europe - who has submitted

Stevan and Florent have submitted two talks:
1. Chefiles talk from EclipseCon France which was very well received;
2. Che 6 features.

Brad is submitting a talk on the current and future state of the IDE market which will touch on Che 6

