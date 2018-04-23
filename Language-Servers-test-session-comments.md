Unfortunately we do not have any functional test specification for covering language servers. For testing we had only simple test cases for covering base functionality based on positive testing. 
The language servers was checked next way:
1. **PHP language server:**
* Create a workspace through Dashboard based on php stack. Enable php LS. by slider on dashboard.
* Go to the just created workspace and create **_web-php-simple_** project with wizard
* Open **_index-php_** file and make sure that language server has been initialized
* Add an error in the `echo` command and check that error marker is appeared. Click on error marker - the proposal widget should be present. Restore content. Error marker should disappear.
* Add variable like `$color = "blue";`. Make sure that there is no errors. Go to the end of `echo "Hello World!"` type `$` and launch autocompletion by Ctrl+Space. The `color` fragment should be completed.
* Set cursor to the new line type `e` and launch autocompletion by Ctrl+Space. Check that proposal is present, see screenshot below:
[swad](https://www.dropbox.com/s/2hrzg04hqbz1a4j/Selection_012.png?dl=0)
