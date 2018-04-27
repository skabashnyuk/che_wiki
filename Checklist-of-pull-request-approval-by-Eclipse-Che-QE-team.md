1. _Definition-Of-Done_ (_DoD_) is clear: feature specification / bug use case described and available for review.
2. If _DoD_ achievement verification requires creation of new **E2E selenium tests** or updating existed ones - they have to be created or updated.
3. Code should has latest changes from the master branch before start **E2E selenium tests**.
4. There are no changes in the code in pull request after **E2E selenium tests** execution was requested.
5. Coverage of new or updated functionality by unit-tests **>= 80%**. We can use [Cobertura maven plugin](https://github.com/cobertura/cobertura) to measure coverage  - next command generate Cobertura report: 
`mvn cobertura:cobertura`
6. Execution of **E2E selenium tests** for_ Eclipse Che Multiuser on OCP_ (command `ci-test` in comment to the pull request to run selenium tests on https://ci.codenvycorp.com/view/pr-builds/job/che-pullrequests-test-ocp/ ) shows:

   6.1 Success rate **about 100%** for existed **E2E selenium tests** without regression;

   6.2 Success rate **equals to 100%** for the new/updated **E2E selenium tests**.

7. If pull request creator decides that changes influence other distributions of _Eclipse Che_, **E2E selenium tests** we should be executed for them as well:

   7.1 Command `ci-test-docker-single` -> _Single-User Eclipse Che on Docker_

   7.2 Command `ci-test-docker-multi` -> _Multi-User Eclipse Che on Docker_ (hasn't been implemented yet https://github.com/eclipse/che/issues/9566)

   7.3 Command `ci-test-ocp-single` -> _Single-User Eclipse Che on OCP_ (hasn't been implemented yet https://github.com/eclipse/che/issues/9567)

8. List of features which are not covered by **E2E selenium tests** will be provided.
