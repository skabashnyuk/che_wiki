##### Command to run E2E selenium tests of creation of workspaces from the stacks within Eclipse Che Dashboard
```
selenium-tests.sh --test=org.eclipse.che.selenium.stack.**
```

##### CI job which is executing the tests daily
https://ci.codenvycorp.com/view/qa/job/che-multiuser-master-ocp-stacks-test/

##### Covered stacks
Can be found in description of [this issue](https://github.com/eclipse/che/issues/10050).