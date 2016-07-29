## Milestone Overview
- [x] New docker image launcher for Che [#1683]
- [x] New lighter image for Che based upon alpine [#1682]

For more information about our development process please see our [development process] (https://github.com/eclipse/che/wiki/Development-Process) page.

## Schedule
This release will be an Eclipse-signed and marketed release  (...or...This release will be an unsigned development release available on GitHub only).
- Code complete milestone: **target July 29**
- GitHub release complete (QA verified) milestone: **target August 2**
- Eclipse signed release complete (IP verified) milestone: **target August 3**
- Release shipped milestone: **target August 4**

### Schedule Detail
#### Code complete milestone
- [ ] Milestone issues complete
- [ ] Announce on che-dev that release endgame has begun - no merges
- [ ] Smoke tests started
- [ ] Release review information sent to Eclipse PMC (only if release will be shipped)
- [ ] IP logs and information sent to Eclipse Foundation (only if release will be shipped)
- [ ] Contribution questionnaires (CQ) approved for all new libraries (only if release will be shipped)

#### Release candidate created milestone
- [ ] Release candidate created
- [ ] Test cycles started
- [ ] Docs reviewed

#### GitHub release complete (QA verified) milestone
- [ ] Release complete
- [ ] Che custom assemblies created (ARTIK + OS)
- [ ] New images (if required) passed to marketing for site
- [ ] Release note blog / email completed
- [ ] Release notes updated
- [ ] Release information updated on GitHub
- [ ] Docs complete and live
- [ ] Announce on che-dev that release is complete - merges allowed

#### Eclipse signed release complete (IP verified) milestone
- [ ] Release signed by Eclipse Foundation
- [ ] Release information updated on Eclipse.org
- [ ] Release uploaded to Eclipse.org servers
- [ ] Release updated on Bitnami
- [ ] Release updated on codenvy.com (Eclipse Che free cloud offering)
- [ ] Public Factories on codenvy.com QA'ed

#### Release shipped milestone
- [ ] Release blog live on che.eclipse.org
- [ ] Marketing email / social notifications

## Target Milestone Issues
The following issues are targeted for inclusion in the milestone. As issues are closed they are checked. Stretch goals are indicated with "*Stretch*" before the item.

#### Epics and Issues
- [x] Add docker image to grab the ip used by docker: https://github.com/eclipse/che/pull/1891
- [x] che-launcher infer Che version and self destruct itself: https://github.com/eclipse/che/pull/1881
- [x] CHE-1535: Reveal resources after move and copy operation: https://github.com/eclipse/che/pull/1877
- [x] Add new parameters to build docker image method: https://github.com/eclipse/che/pull/1872
- [x] Fix new alpine based Dockerfile for Boot2Docker: https://github.com/eclipse/che/pull/1723
- [x] Use a docker launcher image to simplify start/stop/update/restart commands: https://github.com/eclipse/che/pull/1683
- [x] Save machine config with 'dev' instead of 'isDev' field: https://github.com/eclipse/che/pull/1679
- [x] CHE-1248 remove workspace information from EnvironmentContext: https://github.com/eclipse/che/pull/1658
- [x] Update according to changes in everrest: https://github.com/eclipse/che/pull/1625
- [x] Add instructions in new Che launcher how to get Che server logs: https://github.com/eclipse/che/issues/1951
- [x] Automatically open the IDE after creating a project: https://github.com/eclipse/che/pull/1863
- [x] Parameterized Vagrantfile: Make Virtualbox Machine name configurable: https://github.com/eclipse/che/issues/1965
- [x] [Dashboard] fix bug in project template selection: https://github.com/eclipse/che/pull/1737
- [ ] Add CI mechanisms for new Che Docker images: https://github.com/eclipse/che/issues/1842


#### Bugs
- [x]  Stop of Che container in new Che launcher is broken: https://github.com/eclipse/che/issues/1949
- [x] Launcher: fixed Path problems, splitted in 3 files and added tests: https://github.com/eclipse/che/pull/1898
- [x] IDE resources caching from UD is broken: https://github.com/eclipse/che/issues/1909
- [x] [Chefile] Allow to continue to start the script even if there is a chown failure: https://github.com/eclipse/che/pull/1917
- [x] Cannot export a workspace from the Dashboard: https://github.com/eclipse/che/issues/1903
- [x] Copy and paste not working in the terminal: https://github.com/eclipse/che/issues/1899
- [x] Cloning a VSTS repo feature does not work: https://github.com/eclipse/che/issues/1893
- [x] Wrong behavior after configure folder with name 'java' as source: https://github.com/eclipse/che/issues/1814
- [x] Launcher: fixed Path problems, splitted in 3 files and added tests: https://github.com/eclipse/che/pull/1914
- [x] Fix the ENV about configuration folder to set when using docker image: https://github.com/eclipse/che/pull/1896
- [x] Downgrade docker installed in Che image: https://github.com/eclipse/che/pull/1833
- [ ] Docker Launcher - wrong hostname output when running in a VM: https://github.com/eclipse/che/issues/1925
- [x] Restoring a project state after stopping a workspace does not work: https://github.com/eclipse/che/issues/1919
- [x] Unexpected errors in the browser console after restarting a workspace: https://github.com/eclipse/che/issues/1902
- [ ] Path in the 'Parent' field presents incorrectly on the 'Project Configuration' window: https://github.com/eclipse/che/issues/1868
- [x] Opened files list in the editor area does not work properly: https://github.com/eclipse/che/issues/1850
- [x] Change value of "java.output.folder" attribute: https://github.com/eclipse/che/issues/1843
- [x] After closing the Project wizard widget by ESC select path form still opened: https://github.com/eclipse/che/issues/1825
- [x] Delete multi-module projects in some case holding failure: https://github.com/eclipse/che/issues/1819
- [ ] Ws-agent has stopped in some case: https://github.com/eclipse/che/issues/1817
- [x] Tree of 'changes to be performed' in the refactoring 'Rename' window does not work correctly: https://github.com/eclipse/che/issues/1786
- [x] Preview URL may be lost after refreshing page: https://github.com/eclipse/che/issues/1785
- [ ] Websockets are unable to comunicate with the wsagent when the server and the browser run on different networks: https://github.com/eclipse/che/issues/1644
- [x] Remove closed file from the editor's popup list: https://github.com/eclipse/che/pull/1867
- [x] Synchronize project instead of parent directory: https://github.com/eclipse/che/pull/1954
- [x] Che docker launcher incorrectly stops Che server - doesn't respect shut down process. #1949
- [x] Che docker launcher fails if firewalld is activated: https://github.com/eclipse/che/issues/1924
- [x] Not able to run Che as a Docker Container on OSX: https://github.com/eclipse/che/issues/1976
- [x] If use the dashboard for import project from zip archive, the root folder of the archive don't skip: https://github.com/eclipse/che/issues/1852
- [x] Che ignores user response when asks whether it should restore workspace or not: https://github.com/eclipse/che/issues/1849
