Unfortunately we do not have any functional test specification for covering language servers. For testing we had only simple test cases for covering base functionality based on positive testing. 
The language servers was checked next way:
1. **PHP language server:**
* Create a workspace trough Dashboard based on php stack. Enable php LS. by slider on dashboard.
* Go to the just created workspace and create hello php project with wizard
* Open php file and make sure that language server has been initialized
