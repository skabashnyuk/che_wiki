The tests are executed against _Eclipse Che Multiuser_ deployed on _OpenShift_ with set up of _OpenShift OAuth server identity provider_.

To deploy _Eclipse Che on OCP_ properly with **OCP OAuth** configuration we need to use **deploy/openshift/ocp.sh** script with parameter **--setup-ocp-oauth**:
```
bash ${WORKSPACE}/deploy/openshift/ocp.sh --run-ocp --deploy-che --multiuser --setup-ocp-oauth
```

##### Command to run the tests
```
selenium-tests.sh --test=org.eclipse.che.selenium.site.ocpoauth.**
```

##### CI job which is executing the tests daily
https://ci.codenvycorp.com/view/qa/job/che-multiuser-master-ocp-oauth-test/