## TOPICS DISCUSSED:

​1. 5.5.0 status 
2. Blocker bugs
3. Intelligent Commands

## PRIMARY TOPICS

### 5.5.0 status 
We our on schedule to meet release 3/15/17. No concerns at this time.

### Blocker bugs
We currently have a blocker bug based on codenvy.io not responding and having to be restarted. We cannot reproduce or determine exact cause. Will lower severity status if no further occurrences happen. https://github.com/codenvy/infrastructure/issues/76

### Intelligent Commands
Looked at intelligent commands as a group. Provided some UI/UX feedback to developer team. We are still on schedule to start acceptance server that can be used to provide closed beta feedback by the end of this week. We will send invitations via email.

### Roadmap
Tyler discussed roadmap and long term planning of 6-9 months priorities. 

##### ​IDE:
1. Performance of IDE as seen by the user
2. Critical issues as documented by dev
3. LSP advancements - phase II + file extensions?
4. Debugger, debugger, debugger
5. Archetype SDK (lifecycle of custom assemblies)
6. JavaScript IDE client prototype (best effort)

##### Enterprise:
1. (codenvy) Invite by email for SaaS
2. (codenvy) Teams (org mgmt + team ) for on-prem
3. (che) UD re-design for ws create + details + crane
Also want to reduce output for agent boot
4. (che) System stack + template + factory + recipes mgmt
5. (both) Branding customizations & workflow
6. (both) Traffic through a single port (che + codenvy)
7. (codenvy) Per-seat billing for SaaS
8. (codenvy) CC billing for on-prem inside of product
9. (che) Consolidate chefiles + factory JSON 
10. (codenvy) Workspace templates & notifications

##### Infrastructure
1. (both) QE automation
2. (both) Custom images for each branch
3. (codenvy) Codenvy infrastructure on Kube / OpenShift
4. (che) Agent & Machine refactoring
5. (che) Che-in-Che development model
Ability to source ws recipe from a git repo 
Ability to build & run docker from in a ws
6. (both) Workspace live sync concept (airplane mode)