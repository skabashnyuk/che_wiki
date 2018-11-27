The goal of creating this test plan is testing share workspace feature

##  Preconditions:
1. Login in **CHE** as admin.
2. Create an organization.
3. Add a member to the created organization.
4. Create a workspace for this organization.

## Testing process
### Check share workspace feature from workspace owner side
1. Start the workspace and wait that it started successfully.
2. Create a file in the project with any content.
3. On **Dashboard** open workspace details page of the created workspace.
4. Open **Share** tab and invite the member by the **Add Developer** button.
5. Check that admin permissions are ```read, use, run, configure, setPermissions, delete``` and member permissions are ```read, use, run, configure```.
6. Select added developer by checkbox and click on the Delete button.
7. Check that the member deleted from the list.
8. Try to delete admin from list and wait for ```Delete failed.``` error notification.

### Check share workspace feature from member side
1. Invite the member by the **Add Developer** button.
2. Logout admin and login as the member 
3. Check that the shared workspace exists on the **Workspaces** list page.
4. On **Dashboard** open workspace details page of the created workspace.
5. Open **Share** tab.
6. Try to remove workspace owner from the developer list and wait ```User can't edit permissions for this instance``` error notification.
7. Try to delete workspace and wait ```The user does not have permission to delete workspace with id '(workspace id)'``` error notification.
8. Open the workspace and check that the created file exists.
9. Check the file content.