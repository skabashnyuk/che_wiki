Here are the notes of product meeting March 22th, 2016.

######TOPICS DISCUSSED:

1. Status on 4.0
2. Status on C/C++ and GDB
3. Dashboard for 4.1, 4.2 and 4.3
4. Participation from engineers on Eclipse Che public forum and documentation
5. Documentation of pull request

######ACTION ITEMS:
- Document how to document the test issue that may be needed for certain business cases (Brad, Roman, Gennady)


#######IMPORTANT POINTS ON TOPICS DISCUSSED:

**1. Status on 4.0**

* **New VFS - completed**:
Epic closed.
We need docs for the project API. 
QA is still testing it - after the work has been merged

* **Move port from dns to path in case of https**:
No estimate, if we don't have an estimate during the week, we will push it out of 4.0 scope. 
Daily updates needed for this topic.

* **Error of changing hostname of Codenvy on-prem AIO**:
Investigation in progress / Still looking for the root cause


Brad need to create some issues reported by beta customers. 



**2. Status on C/C++ and GDB**

* **C/C++**:
C/C++ and python for vitalii (syntax coloring - stevan sent icons to vitalii)

* **GDB**:
Anatoliy working on GDB debugger. Working on adding the commands on the server. First prototype of C/C++ debugger - in 1/2 weeks
Check what languages GDB is allowing debug.


**3. Review of 4.1 Goals**

* **Codenvy SaaS Phase1**:
 * CODENVY-197: Analytics for OnPrem - has been switched to an epic no needed for 

 * CODENVY-282: Workspace agent could not start after long pause in work - this problem is reported by customers and we need to notify the user about this particular use case. Add a notification when the workspace agent is not connected anymore with the workspace master.


 * CODENVY-303: Notify user in IDE of unavailable workspace - show a notification when the workspace is stopped or wbsocket connection is broken, disconnected. Brad will provide the messages.
Will be needed in Dashboard too - but primarily in IDE.
Issue for Vitalii.


**4. Participation from engineers on Eclipse Che public forum and documentation**

Start thinking about the developer docs.

The engineering team reported that for the time being, the model is evolving very quickly and instead of providing docs that is not accurate, it is somehow better to not have docs.
We know that we have to better handle our developer docs and this topic will be discussed internally to define initial ways to provide more and accurate docs.

**5. Documentation on PR**

*More documentation needed for PRs : exemple PR-765*
We need to give a look on the how the other open source projects are requiring documentation on the Pull Requests. 


**6. Next Sprint pre-planning**

For the upcoming sprint we handled pre-planning session where we discussed about the upcoming priorities and clarify all issues that needed to be analyzed. 