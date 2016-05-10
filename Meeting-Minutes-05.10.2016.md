Here are the notes of product meeting May 10th, 2016.

######TOPICS DISCUSSED:

1. Status of beta.codenvy.com 
2. Status of 4.3
3. Plug-in resources center
4. Adding the new navigation concept to objective of Q2
5. Docker partner beta program
6. Default Dockerfile
7. Snapshots and default workspace flows
8. General questions

######ACTION ITEMS:



######IMPORTANT POINTS ON TOPICS DISCUSSED:


**1. Status of beta.codenvy.com**

beta.codenvy.com is much more stable.
Interested to know what happened yesterday. Did we found a solution? 

Swarm give us wrong outputs in comparison to what we were expecting. 
We were not catching the correct outputs. One of the node had an error and swarm send a new kind of outputs, which we were not expecting.
Swarm does not have machine friendly messages.

We will have a pingdom script and alerts to test the status of beta.codenvy.com.


**2. Status of 4.3**

Scope has been refined and simplified over last week.

Permission work:
- we are going to ship 4.3 with what we have + changes related to stacks and recipe.
- move to 4.4 the rest
- plan UI work for 4.4

**3. Plug-in resource center**

We'll have a first iteration done for tomorrow. We'll ask various engineers to review, comments and give some feedbacks.
The goal is to be ready to publish a first version along with 4.3

*Setup workspace within Eclipse:*
One of the biggest issue we have at this moment is the setup of workspace within Eclipse. We should definitely improve that. Potential solutions:
- having few dev using eclipse
- eclipse oomph profile

**4. Adding new left-navigation as goal for Q2**

In order to improve the consistency and the UX of the navigation between dashboard and IDE, we are going to introduce a new navigation concept: a left navbar always available, either on dashboard or in the IDE.
The left navbar will allow to jump into the recent opened workspaces. The transition between the IDE and the dashboard will be improved and happen seamlessly.
The loading experience for stopped workspace will happen inside of the IDE.



**5. Docker partner beta program**

Invited to be part of the beta program due to the nunmber of downloads our images are having. 
We'll have few enigneers involved in the beta program.

**6. Default Dockerfile**

Eugene is has done a great job on the Che dockerfile to make it better. We agreed that the future is to run Che as a docker container as root solution. All of us are going to use this deployment method. 

**7. Snapshots and default workspace flows**

We discussed various technical challenges that we are having with Docker Swarm, when we use snpashots mecanism.
- Snapshots with multiple nodes are not working properly with Swarm
- experience will be horrible for users.

We can't control where the Swarm will create a container (in which node)

We agreed that we will provide snapshots mecanism without registry for Che and continue to study for Codenvy the various solutions we may have.

**8. General questions**
- Eugene: allowing users to delete account by themselves. --> Sergey for Q3
