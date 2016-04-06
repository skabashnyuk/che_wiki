Here are the notes of product meeting April 5th, 2016.

######TOPICS DISCUSSED:

1. Beta.codenvy.com and status of 4.1
2. Policies for workspaces and timeouts
3. Status on C/C++, GDB and Targets
4. Blogging strategy


######ACTION ITEMS:
- Document use cases when policies limitation can happen (Stevan)
- Document requirement for per account policies (Brad)
- Add new docker images created as ready-to-go stacks (Eugene)


#######IMPORTANT POINTS ON TOPICS DISCUSSED:

**1. Beta.codenvy.com and status of 4.1**

We have some bugs with the autostop features on workspaces. They are in progress and those flows are tested by QA. 

A lot of changes have been merged on master and there is a risk that a new bunch of bugs are raised by QA during the release process. 

We will release 4.1 as soon as possible in order to allow partners to start creating factories.

* **CHE-922**
We cannot create new folder to projects inside of projects. 
Don't work on 4.0

* **CHE-880** 
Very urgent - Anna is working on it.

* **CHE-897**
Done

* **SVN in 4.1**
It was merged in master. 

* **OpenSources factories**
Florent is polishing a first version of the flow which will be included in 4.1

**2. Policies for workspaces and timeouts**

We will decrease the number of workspaces ram.
- Max ram usage of 3GB at one time 
- No limits on workspaces

We'll use the following params:
- $limits_user_workspaces_count = "999999999" # A LOT!
- $limits_user_workspaces_ram = "3gb"
- $limits_workspace_env_ram = "3gb"
- $machine_ws_agent_inactive_stop_timeout_ms = "600000"

Timeouts policies:
- workspaces are by default  not always-on. All workspaces have an idle timeout
- At this moment we have a timeout of 10minutes after the last api touch on the workspace agent.

Ressource limitation per account will be the work to be done after. Brad will create an issue.

Stevan need to figure out what are the use cases (workspace creation + factory) what will be the messages to display.


**3. Signing Che**

We still have an issue when we are signing the Eclipse Che binaries at Eclipse. are waiting a response about guiceCODENVY-338

We are still waiting response from guice: https://github.com/google/guice/issues/1006.

If we don't have the answser, we'll have to figure out another solution.



**3. Status on C/C++, GDB and Targets**

* **UI**:

Edit targets, management of machines are in progress. 
Expecting a demo end of the week. 

Consoles:
we will be able to show all machines.

Samples and stacks:
- Eugene is creating a dedicated instance on Digital Ocean.
- C sample and Python
-- they have cross compilation on 
-- they have GDB

* **C/C++**:

C/C++ and python for vitalii (syntax coloring - stevan sent icons to vitalii)

* **GDB**:

The integration of GDB has been done - the remaining work is on adding the tests. 

**4. Blogging stragety**
https://docs.google.com/spreadsheets/d/1QMTI9CSzo65O79sfhhNM8mdRFzgzDeIoZsAMYJAS18E/edit#gid=0

Everybody in the office will have to write a blog.
Full week to find a topic and start working on a particular topic to be blogged.
This work will be planned in the sprint.

It can be related to any kind of topic: Che/Codenvy/Docker/Selenium...
Informative, educational and very simple.

To make it simpler and aligned with our sprints, the weeks will started from wednesday to wednesday.