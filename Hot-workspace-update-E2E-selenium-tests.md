### Rolling Workspace Update Strategy tests
Are executed against _Eclipse Che Multiuser_ deployed on _OpenShift_ with _Rolling Update Strategy_.

To deploy _Eclipse Che_ with **Rolling Update Strategy** we should pre-set system environment variable: 
```
export UPDATE_STRATEGY=Rolling
```

##### Command to run Rolling Workspace Update E2E selenium tests:
```
selenium-tests.sh --test=org.eclipse.che.selenium.hotupdate.rolling.**
```

##### CI job which is executing the tests daily
https://ci.codenvycorp.com/view/qa/job/che-multiuser-master-ocp-rolling-strategy-test/

### Recreate Workspace Update Strategy tests
Are executed against _Eclipse Che Multiuser_ deployed on _OpenShift_ with _Recreate Update Strategy_.

To deploy _Eclipse Che_ with **Recreate Update Strategy** we should pre-set system environment variable: 
```
export UPDATE_STRATEGY=Recreate
```

##### Command to run Recreate Workspace Update E2E selenium tests:
```
selenium-tests.sh --test=org.eclipse.che.selenium.hotupdate.recreate.**
```

##### CI job which is executing the tests daily
https://ci.codenvycorp.com/view/qa/job/che-multiuser-master-ocp-recreate-strategy-test/