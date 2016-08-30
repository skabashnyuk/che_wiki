This roadmap acts as a 6-9 month forward-looking expectation of what we are working to incorporate into Eclipse Che. This roadmap is thematic tied to our three core audiences: a) users (developers), b) customizers (ISVs), and c) deployers (enterprises / teams). We schedule release milestones on a functionality basis with 2-3 milestones scheduled in advance. The length of a milestone is unknown, but we attempt to keep it less than a month and sometimes as short as 2 weeks. We map the epics implemented from the roadmap into each milestone. The epics and features that roll into a milestone are determined by pull request readiness of the feature at the time a milestone begins. In other words, we only place into a milestone features that are code complete and waiting for master-integration and testing.

## Users: Simplify the Getting Started Experience
Eclipse Che should install anywhere and be easy to install. It should also be possible for you to get a project-typed workspace with a custom set of commands in a natural, minimal sequence. Eclipse Che should become context-aware and auto-generate workspaces with type and code information based upon the contents of directory or repository.
- [x] Make docker the default execution for Che. [#1683](https://github.com/eclipse/che/pull/1683)
- [ ] Add support for the Codenvy / Red Hat / Microsoft language server protocol [#1287](https://github.com/eclipse/che/issues/1287)
- [x] "Code in Che" from any git repository [#1895](https://github.com/eclipse/che/issues/1895)
- [x] Second phase of "Code in Che" from any git repository [#2266](#2266)
- [ ] Simplify dashboard navigation to eliminate unnecessary clicks [#1743](https://github.com/eclipse/che/issues/1743) 
- [x] Move dashboard navigation to list layout [#1762](https://github.com/eclipse/che/issues/1762)
- [x] Move workspace editing to form layout [#1767](https://github.com/eclipse/che/issues/1767)
- [x] Support `/namespace/workspace` URL access [#1572](https://github.com/eclipse/che/pull/1572)
- [x] Split view for editor [#1837](https://github.com/eclipse/che/issues/1837)
- [ ] Make it possible to add / remove servers without customizing a Dockerfile
- [ ] Provide image project type to simplify edit, build, debug of images
- [ ] Ability to preview HTML files [#1883](https://github.com/eclipse/che/issues/1883)

## Customizers: Make Customizations More Approachable
Eclipse Che should be easy to customize. Che has many customization points including stacks, templates, extensions, plugins, assemblies, and commands. Where possible, we should make these customizations happen within Che's dashboard or as a project type within the IDE. For assembly-related items, such as custom stacks, Che should be self-updating and dynamic for the addition and removal of items. For extension-related items, such as the IDE, Che should have a simple way to get started developing plug-ins with incremental builds and, if necessary, super dev modes. The project must also evolve its interfaces to support community projects to create value-added layers within Che such as ecore, EMF, GMF, and multi-cursor editing.

- [ ] Add, edit, and delete templates and stacks from the dashboard [epic:2205](#2205)
- [ ] Localhost machines, to create workspaces without Docker on the host
- [ ] Simpler Che-in-Che scenarios [epic:2116](https://github.com/eclipse/che/issues/2116)
- [x] Provide docker images for building Che to reduce configuration [See wiki](https://github.com/eclipse/che/wiki/Development-Workflow#build-che-using-docker)
- [ ] Dynamic file watchers with events to auto-update IDEs when workspace files are edited out of band [#1824](https://github.com/eclipse/che/issues/1824)
- [ ] JPA data access implementation to store information with in-memory databases [#1790](https://github.com/eclipse/che/issues/1790)
- [ ] Make it easier for third party tools to integrate Che [#1894](https://github.com/eclipse/che/issues/1894)

## Enterprises: Expand Che Execution Scenarios
Che needs to run in a variety of environments and support large-scale workspace consumption in an elastic way. There needs to be a clear, prescriptive set of controls for admins who adminster Che systems. We will enable multi-node elasticity in Che, and we will defer multi-user, multi-tenant, and organizational implementations to commercial vendors building more advanced versions of Che.
- [ ] Allow off-the-shelf docker images to work within Che [#1823](https://github.com/eclipse/che/issues/1823)
- [ ] Dynamic injection of workspace agents [#1823](https://github.com/eclipse/che/issues/1823)
- [ ] Start a new workspace with a Docker compose definition
- [ ] Switch between different runtime environments in a single workspace
- [ ] Environment SPI, to allow platform providers like OpenShift to create plugins to manage workspace runtimes [#1829](https://github.com/eclipse/che/issues/1829)
- [ ] Che with a reverse proxy to minimize port exposure (workspace URLs will be embedded) [#1560](https://github.com/eclipse/che/issues/1560)