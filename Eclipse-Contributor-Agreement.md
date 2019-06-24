You must sign an Eclipse Contributor Agreement (ELA) before your PR will be merged. This a one-time requirement for Eclipse projects in GitHub. You can read more about what Eclipse Contributor Agreement (ELA) is on [ECA FAQ](https://www.eclipse.org/legal/ecafaq.php).

However, you don't have to do this up-front. You can simply clone, fork, and submit your pull-request as usual. Signing the ECA might sound scary but it's actually very simple and can be done in less than a minute.

To sign the Eclipse Contributor Agreement, [log in to the Eclipse projects forge](http://www.eclipse.org/contribute/cla). You will need to create an account with the Eclipse Foundation. Click on "Eclipse Contributor Agreement", and complete the form. Be sure to use the same email address in your Eclipse account that you intend to use when you commit to Git.

Signed Commits
--------------
All commits to Eclipse Che [should be signed off](https://wiki.eclipse.org/Development_Resources/Contributing_via_Git#Signing_off_on_a_commit) with the email used to accept the Eclipse Contributor Agreement.  


Making your Pull Request ECA compliant
--------------------------------------
There is a bot that is checking that every pull request is provided by an author with approved ECA. If you did a pull request and seeing an error in the ECA checker, you need to make sure that your commits have been signed-off. In your commits you should see: 

`Signed-off-by: Name <your-eca-email>`

The text can either be manually added to your commit body, or you can add either **-s** or **--signoff** to your usual git commit commands. If you forget to add the sign-off you can also amend a previous commit with the sign-off by running `git commit --amend -s`. If you've pushed your changes to Github already you'll need to force push your pull request branch after this with `git push -f`. 
