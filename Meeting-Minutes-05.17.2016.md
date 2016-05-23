Here are the notes of product meeting May 17th, 2016.

######TOPICS DISCUSSED:

1. Review beta.codenvy.com
2. Review 4.3
3. Plug-in resources center
4. General questions

######ACTION ITEMS:
- Viktor + Sergey: CHE-1158 to be splitted in two separate tasks (one for system scope / user scope)


######IMPORTANT POINTS ON TOPICS DISCUSSED:

**1. Status of beta.codenvy.com and bug fix releases**

Bug fix release for CODENVY-469 / CODENVY-470 by wednesday. 

Next another bug fixe release will be about:
* Ability to use an image on a private Docker registry,
* Support forDocker mirror support (download in a local docker repo, like a proxy with cache). We will support the system wide scope at initial step, per user/account in a second time.


**2. Status of 4.3**

- Work on SVN is going to be completed.
- Permissions for Codenvy are ready to be merged
- New Maven / Java plug-ins are merged - working on some regressions and bugs found by QA

**Language tooling**  
We'll probably have a new piece for into our tooling to support all kind of new languages and provide intellisense. If it's ready to 4.3, we will include it. 


**3. Plug-in resource center**  

We'll have a first iteration done for tomorrow. We'll ask various engineers to review, comments and give some feedbacks.
The goal is to be ready to publish a first version along with 4.3

*Setup workspace within Eclipse:*
One of the biggest issue we have at this moment is the setup of workspace within Eclipse. We should definitely improve that. Potential solutions:
- having few dev using eclipse
- eclipse oomph profile



**4. General questions**
- Eugene: allowing users to delete account by themselves. --> Sergey will add that as objective for Q3