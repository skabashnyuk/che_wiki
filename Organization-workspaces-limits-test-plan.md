The goal of creating this test plan is testing an organization workspaces limits 

### Planed to do 
Test next workspaces limits for members in an organization:
* **Workspace Cap** - maximum number of workspaces for the organization. 
* **Running Workspace Cap** - maximum number of running workspaces for each organization
* **Workspace RAM Cap** - maximum RAM organization workspaces can use.

## Testing process

1. Login in CHE as admin
2. Create an organization
3. Open the Settings tab on organization details page
4. Set next values for limit caps:
Workspace Cap: 2
Running Workspace Cap: 1
Workspace RAM Cap: 2
5. Add a member to the created organization
6. Login as member

### Workspace Cap:
Create two workspaces from the Java stack with 2GB RAM each
Try to create the third workspace and wait ```You are not allowed to create more workspaces.``` error notification

### Running Workspace Cap:
Start one of the created workspace and wait that the workspace started successfully 
Try to start other workspace and check ```You are not allowed to start more workspaces.``` error notification
Stop started workspace

### Workspace RAM Cap:
Open workspace details page of any workspace and change RAM value in the Machines tab to 3GB
Try to start this workspace and check ```Workspace (org/name) needs 3072MB to start. Your account has 2048MB available and 0MB in use. The workspace can't be start. Stop other workspaces or grant more resources.``` error notification.