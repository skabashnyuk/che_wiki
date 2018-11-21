1. _Definition-Of-Done_ (_DoD_) is clear: feature specification / bug use case described and available for review.
2. If _DoD_ achievement verification requires creation of new **E2E selenium tests** or updating existed ones - they have to be created or updated.
3. Code should has latest changes from the master branch before start **E2E selenium tests**.
4. There are no changes in the code in pull request after **E2E selenium tests** execution was requested.
5. Coverage of new or updated functionality by unit-tests **>= 80%**. We can use [Cobertura maven plugin](https://github.com/cobertura/cobertura) to measure coverage  - next command generate Cobertura report: 
`mvn cobertura:cobertura`
6. Build of whole project including unit and integration tests has passed successfully. It can be checked by command `ci-build` in comment of pull reauest, which run build on [dedicated CI job]9https://ci.codenvycorp.com/view/pr-builds/job/che-pullrequests-build/).
7. Execution of **E2E selenium tests** for _Eclipse Che Multiuser on OCP_ (command `ci-test` in comment to the pull request to run selenium tests on [dedicated CI job](https://ci.codenvycorp.com/view/pr-builds/job/che-pullrequests-test-ocp/)) shows no regression, that is success rate **about 100%**. Such execution doesn't include tests which fail because of known issue. "flaky" tests has been restarted once.

8. If pull request creator decides that changes influence assembly of _Eclipse Che_ on Docker, **E2E selenium tests** should be executed against Eclipse Che on Docker as well - by using another the command `ci-test-docker-single`, which run build on [another CI job](https://ci.codenvycorp.com/view/pr-builds/job/che-pullrequests-test/).

9. Actually, **E2E selenium tests** cover about 50% of functionality of Eclipse Che upstream. There is a [list of features which are not covered by **E2E selenium tests**](https://github.com/eclipse/che/wiki/List-of-Eclipse-Che-6-features-which-haven't-been-covered-by-selenium-tests-yet).

10. There are some tests which require special configuration of product, or are executing to long, and so don't run by **ci-test** commands on _Pull Requests_:
- [Hot workspace update E2E selenium tests](https://github.com/eclipse/che/wiki/E2E-selenium-tests:-Hot-workspace-update)
- [Creation of OpenShift objects under the current user account on OCP E2E selenium tests](https://github.com/eclipse/che/wiki/E2E-selenium-tests:-creation-of-OpenShift-objects-under-the-current-user-account-on-OCP)
- [Creation of workspaces from stacks from within Eclipse Che Dashboard](https://github.com/eclipse/che/wiki/E2E-selenium-tests:-creation-of-workspaces-from-stacks).
