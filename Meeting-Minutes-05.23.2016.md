Here are the notes of product meeting May 23th, 2016.

######TOPICS DISCUSSED:

1. Review 4.3
2. Discuss 4.4 and getting codenvy.com updated with 4.x
3. API Changes documentation

######ACTION ITEMS:
- Stevan: CODENVY-56: split into two separate issues  
- Sergey: CODENVY-56: Need to get a feedback on what is the fatest path to get the remaining issues for 4.3. Sergy to plan internal meeting on that  
- Tyler: re-test the issue CODENVY-491
- Team: resync on wednesday for 4.3 
- Stevan: plan a meeting about codenvy.com


######IMPORTANT POINTS ON TOPICS DISCUSSED:

**1. Status of 4.3**

- Permissions  
We are missing an important part related to the handling of the permission with the workspace to allow another user to access if he has been given the right permissions. 
Similarly, permissions are going to be applied to the workspace's runtime. This was planned for a second time but appear as very important piece for 4.3
A separate call will be planned on this topic to decide which action to take. We'll study the impact and the fatest path to get those items done.

- Openshift plug-in not able to build
We will have a specific assembly for Openshift

https://jira.codenvycorp.com/browse/CODENVY-491:


When can we release:
- beginning on next week - next tuesday would be ideal


**2. Discuss 4.4 and getting codenvy.com updated with 4.x**

4.4 will be lighter release focused on:
- new navigation pattern with a left sidebar consistent accross the IDE and the Dashboard. 
- Security improvements
- Transition of codenvy.com to use 4.x

As soon as we will approach 

**3. API Changes documentation**

We discuss about the need of documenting the API changes and referencing as part of our release process. We will document the impact changes on the API that may impact the consumers. The changes can be: deprecation, removal, improvements

We will add that as part of our contribution rules. We will setup rules for each PR to provide the needed description of the changes on API. 
