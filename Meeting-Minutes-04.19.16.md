Here are the notes of product meeting April 19th, 2016.

######TOPICS DISCUSSED:

1. Status of beta.codenvy.com
2. Status of 4.2
3. Factories
4. Update on Events
5. Maven plug-in and 4.3 stability



######ACTION ITEMS:
- Create issue to automate tests for beta.codenvy.com similar to what we have on codenvy.com (stevan)
- Release - Tag 4.1.1 release on eclipse-che (stevan)
- Update 4.3 backlog and plan (stevan)



#######IMPORTANT POINTS ON TOPICS DISCUSSED:


**1. Status of beta.codenvy.com**

beta.codenvy.com seems to get some stability issues.
Marketing push for 4.1 is expected to be wednesday AM (US timezone)

- Why instances are going crazy? 
1st problem due to out of space with logs. 
2nd some problems with azure - disks just became broken on the system...

We head dump and cleaned - and restarting.

Are we able to get alert when something is going crazy? 
- Roman: think that we are able to get the information / maybe reported by zabbix

Marketing for 4.1 is planned for wednesday morning. Team will provide the feedback about the state of beta.codenvy.com before the marketing push. 

Beta doesn't not have automated test setup - we will need to setup that.


**1. Status of 4.2**

4.2 has to be ready for the release thrusday morning.
4.2 will be ship on friday

Review will be done on thursday afternoon.

We discussed the way the repository are structured to handle various customer cases. Our current organization is requiring packaging for each customers, which means that we have to keep all the repo in sync. There are some investigations in progress in order to simplify that and have a better approach. 

We will provide doc on how to fork and create a custom assembly for a particular use case (implementing a plug-in for example).

**3. Factories**

We use factories as a way for Che community to discover Che without having to install anything. They can try Che on our public cloud for a wide range of technologies.
https://www.eclipse.org/che/getting-started/

Separately, people are now able to test the export to cloud features.

We are thinking about ways to structure the list of factories between samples code and technologies/frameworks

**4. Update on Events**


We will have to publish on the website/blog the list of the upcoming events where we will be. (action bill/brad)

JUGs: very interesting feedback and people who are joining the event have played with Che before. They learn more and directly see the potential.
Good questions from the audience. One that is recurrent, is about:
- when we will make our system compatible with Docker Compose?

This week we will have devoxx, our goal is to reach as many people as we can to create open source factories. We will have a form on the booth so that the people can send us their repo and info and we can reach them.


**5. Maven Plug-in**

https://jira.codenvycorp.com/browse/CHE-229

As soon as 4.2 is released, feature branches for Maven and Permissions will be merged on master. 

We agreed to get a minimal scope on 4.3 with Maven Plug-in, Java Improvements and Permissions.