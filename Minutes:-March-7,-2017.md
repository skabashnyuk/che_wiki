## TOPICS DISCUSSED:

​1. 5.5.0 status  
2. Blocker bugs  
3. Intelligent Commands  
4. Roadmap

## PRIMARY TOPICS

### 5.5.0 status 
We our on schedule to meet release 3/15/17. No concerns at this time.

### Blocker bugs
We currently have a blocker bug based on codenvy.io not responding and having to be restarted. We cannot reproduce or determine exact cause. Will lower severity status if no further occurrences happen. https://github.com/codenvy/infrastructure/issues/76

### Intelligent Commands
Looked at intelligent commands as a group. Provided some UI/UX feedback to developer team. We are still on schedule to start acceptance server that can be used to provide closed beta feedback by the end of this week. We will send invitations via email.

### Roadmap
Tyler discussed roadmap and long term planning of 6-9 months priorities. 

#### ​IDE:
1. Performance of IDE as seen by the user
2. Critical issues as documented by dev
3. LSP advancements - phase II + file extensions?
4. Debugger, debugger, debugger
5. Archetype SDK (lifecycle of custom assemblies)
6. JavaScript IDE client prototype (best effort)

#### Enterprise:
1. UD re-design for ws create + details + crane
  - Also want to reduce output for agent boot
2. System stack + template + factory + recipes mgmt
3. Branding customizations & workflow
4. Traffic through a single port
5. Consolidate chefiles + factory JSON 

#### Infrastructure
1. QE automation
2. Custom images for each branch
3. Agent & Machine refactoring
4. Che-in-Che development model
  - Ability to source ws recipe from a git repo 
  - Ability to build & run docker from in a ws
5. Workspace live sync concept (airplane mode)