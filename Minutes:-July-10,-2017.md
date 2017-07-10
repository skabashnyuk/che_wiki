# PARTICIPANTS:

Gennady Azarenkov
Florent Benoit
Gorkem Erkan
Roman Iuvshyn
Eugene Ivantsov
Alexander Garagatyi
Stevan LeMeur
Mario Loriedo
Vitalii Parfonov
Anna Shumilova

# TOPICS DISCUSSED:

1. Review the Development Process document
2. Using github CODEOWNERS file in eclipse/che
3. CI PRs jobs fails randomly ([gh issue](https://github.com/eclipse/che/issues/5555))
4. Che 6
5. Porting codenvy gh issues to eclipse/che
6. Containers' market map
7. Codenvy Slack
8. Che Loading Sequence
9. Automating changelog generation

# Detailed minute:

### Review the Development Process document

- Reviewers should verify the quality of PR on the following 3 aspects: code, test and documentation
- Updating QA scripts can or cannot part of the PRs. The policy is decided by the maintainer.
- Triage on PR should be automated with a bot and maintainers should periodically review PRs assigned to them
- It would be nice to have metrics about eclipse/che issues and PRs 
- Maintainer responsibility is about scheduling the work and communicating about the PRs
- Triage for issues is support responsibility, not maintainers
- Red Hat internal process should not be part of the document

### Using github CODEOWNERS file
- Roman will take care of it. Fine grained (one for each component) is a nice to have.

### CI PR jobs fails https://github.com/eclipse/che/issues/5555 randomly
- Roman reported that and already created a issue for that. Platform should have a look at that.

### Che 6 beta plan:
The plan will in master with at least + fucntional test by the end of next sprint
The new features won't be merged until openshift connetor is not working with SPI anymore
Keycloack integration should be not dependent by the SPI so that we can ship it even if the SPI is not shipped. OpenShift connector end2end tests should be added to validate a build.

Almost all the funtionalities except User Dashboard are working now (new IDE, new SPI and WS loading). This week functional tests will be updated too. The plan is to have everything working by the end of the next Sprint (~1 month).

OpenShift Connector should be tested before merging features (e.g. SPI) in master.

Keycloack port should be independent from the SPI branch (we should be able to ship keycloack without the SPI if needed)

We should include OpenShift connector end to end test to current eclipse/che release validation tests.

### When (& how) do we move all issues with eclipse-che label from codenvy repo to Che repo?
We can use a tool like [github issue mover](https://github-issue-mover.appspot.com/) but it may be esier to just have a look at how many issues really need to be ported. Label eclipse/che has already been added to some issues to facilitate the work. Stevan will take the action.

### Reviewers needed for updated container market map
Old version is here: https://codenvy.com/resources/market-map/Codenvy-Market-Map-Spring-2016.pdf, if someone is interested in reviewing contact Brad.

### What is left to shut down Slack, update che site with removal of gitter, etc, and letting public/customers roll into mattermost?
Keep slack for customers for now. Switch to free version of Slack can be an option now that almost everything has been moved to mattermost. We cannot use chat.openshift.io for customers yet (red hat email needed).

### Follow-up on loading sequence and opened discussion from May
Stevan will send an email about that

### Changelog - Is it necessary? Generate it from tool?
It's necessary and we should go back to the GitHub changelog generator. In order to do that the issues and PRs titles should correspond to the Changelog. Reviewers should verify/enforce that during the review.