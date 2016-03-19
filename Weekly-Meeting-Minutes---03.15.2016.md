Here are the notes of product meeting March 15th, 2016.

######TOPICS DISCUSSED:

1. Follow-up post EclipseCon
2. Status on 4.0
3. Dashboard for 4.1
4. Next Sprint pre-planning

######ACTION ITEMS:
- Document how to document the test issue that may be needed for certain business cases (Brad, Roman, Gennady)
- Investigate replicated.com, see the installer and how it works to see if there are any things that we could do (Roman + Sergey)
- Cleanup backlog for 4.1 - 4.2 - 4.3 (Stévan)
- See how we can organize the weekly product call to get Anna with us (Anna, Gennady, Stevan)
- Need to check the impacts of upgrading a local Che without the Project API changes for new VFS to a version with it (Vitali)


#######IMPORTANT POINTS ON TOPICS DISCUSSED:

**1. Follow up post EclipseCon**

The keynote went really nice and have been a great success for Eclipse Che.
The number of visitors on eclipse.org/che and the number of downloads have never been that high. As for now, those number are staying pretty high, which is a very good sign. 

During the Con, we had numbers of people coming to us to ask about how to build custom plugins. They are seeing us as a platform that their own tools need to be integrated with and which can provide advanced set of new features and use cases. 

**2. Status on 4.0 GA for Codenvy**

As for now, it seems that the only work that is remaining is pretty small and we are close to be able to ship 4.0. This could happen during the upcoming 2 weeks.

* **Rework Project API with new VFS**

Almost done, acceptance is updated with (a10) for testing purposes. In general we are really close to merge it. Several days to make more tests and get the go from QA. 
Need to check the impacts if you are upgrading from a Che without the new VFS. 
About performance impact? 
- We have not run performance tests
- When opening a project with a large project tree, then the performances are better - but we think that we have other sort of incremental improves to do.
Expected to be merged this week.


* **Enhanced silky smooth loadings and transitions experience**

Animation has been merged for the case of creating a new project. We have some refinements to do on the crane loader + handle the case of starting a stopped workspace.

* **LDAP connectivity for - Codenvy 4 OnPrem** 

Codenvy 4.0 will not support Custom LDAP. It will support only LDAP schema as we are using on our side. https://tools.ietf.org/html/rfc2798

* **PR for CHE-379**

This issue is about merging Settings and Preferences and needs to be discussed between Viktor and Stévan.

**3. Scope for 4.1 and 4.2**

We decide to make 4.1 focus only on getting ready for Codenvy SaaS Phase 1.
All the other issues will move to 4.2, if they get done before we ship 4.1, then we will merge them into master and label them with the fixVersion 4.1.

**4. Next Sprint pre-planning**

For the upcoming sprint we will run as usual with proposal from team. For the next ones, we will have sessions to prepare the sprint much ahead they start.