The goal of creating this test plan is testing share workspace feature

## Planed to do 
Test next 

##  Preconditions:
1. Login in **CHE** as admin
2. Create an organization
3. Add a member to the created organization
4. Create a workspace for this organization

## Testing process
### Check share workspace feature from workspace owner side
1. Start the workspace and wait that it started successfully
2. Create a file in the project with any content
3. On **Dashboard** open workspace details page of the created workspace
4. Open **Share** tab and invite the member by the **Add Developer** button
...permission...


Logout admin
### Check share workspace feature from member side
1. Login as the developer and check that the shared workspace exists on the **Workspaces** list page
2. On **Dashboard** open workspace details page of the created workspace
3. Open **Share** tab
4. Try to remove workspace owner from the developer list and wait ```User can't edit permissions for this instance``` error notification
5. Try to delete workspace and wait ```The user does not have permission to delete workspace with id '(workspace id)'``` error notification
6. Open the workspace and check that the created file exists
7. Check the file content