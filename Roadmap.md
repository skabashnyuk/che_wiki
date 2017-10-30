This roadmap is a 6-9 month forward-looking expectation of what we plan to include in Eclipse Che. 

This roadmap is thematically tied to three audiences: 
1. Users (developers) 
1. Ecosystem (ISVs) 
1. Admins (enterprises / teams) 
1. Che-Dev (development community)

Releases occur every three weeks. While working on a current release, we plan the following release. We thematically break the major functionality into epics that have sub-issues that can span many sprints, and sometimes across many releases. We do our best to incorporate all of feature into a single release, but it often requires that we break functionality across multiple release milestones.

The epics and features that roll into a milestone are determined by pull request readiness of the feature at the time a milestone begins. In other words, we only place into a milestone features that are code complete and waiting for master-integration and testing.

# August 2017 Update: Multi-User, Multi-Tenant Che
We have witnessed a strong need from downstream projects to have a multi-user, multi-tenant Che:

1. codenvy.io, in its push to replace Swarm infrastructure
2. Red Hat OpenShift.io, a devops solution based upon OpenShift
3. SAP Hana, in their investigation for upgrading from Che 3 

The Che 6 plan (below) has these features included along with a broader ambition to redesign the IDE, introduce an infrastructure SPI, and include a number of new developer features within the IDE itself.

We are investigating an intermediate release on the Che 5 branch that introduces a multi-user, multi-tenant version of Che on OpenShift. 

The 5.x release will:
1. Include the OpenShift adapter built by Red Hat.
2. Certified for Docker and OpenShift, but not yet Kubernetes.
3. Replace Codenvy's authentication with Keycloak.
4. Move the elements for teams, groups, and permissions from Codenvy into Che (including UD).
5. Support multi-tenancy of the Che server on OpenShift.

Most of this engineering work is well scoped and will likely be done within the next 1-2 sprints. However, our engineering teams are making a number of assumptions about how authentication and authorization should work with Keycloak and we need to validate these assumptions in the real world. We will hold on a formal release until we have verification that codenvy.io and OpenShift.io downstream projects have successfully deployed this new solution at scale and we can produce a runbook that guides others wanting to run Che at scale. We may learn that certain design assumptions are invalidated by these deployment that cause us to have another couple sprint engineering cycle.

# Che 6
Eclipse Che should provide a developer experience that rivals world-class tools such as the Eclipse IDE and JetBrains.  Workspaces should be configurable to work with any kind of language and have best-in-class support for the language server protocol along with packaging all known language servers. Users must be able to perform any action using a unified command palette. VCS experience should be simpler and better integrated in the IDE. Navigating into source code, searching and performing actions accross multiple files should also become more natural and designed for efficiency. These needs will also involve an important work on the UI and the UX for the IDE.

## Professional Development Tool
- [ ] Reliable Java tooling for class deletion/renaming/moving [#5013](https://github.com/eclipse/che/issues/5013), [#4979](https://github.com/eclipse/che/issues/4979), [#3928](https://github.com/eclipse/che/issues/3928)
- [ ] Efficient source code navigation (search and class navigation) [#1564](https://github.com/eclipse/che/issues/1564), [#4577](https://github.com/eclipse/che/issues/4577)
- [ ] Typescript Support (code completion, errors and syntax highlighting, formatting, refactoring and code navigation) [#5146](https://github.com/eclipse/che/issues/5146)
- [ ] Improved unit tests support [#4994](https://github.com/eclipse/che/issues/4994), [#4980](https://github.com/eclipse/che/issues/4980)
- [ ] _(best effort)_ Debugger with thread support [#2611](https://github.com/eclipse/che/issues/2611)
- [ ] _(best effort)_ Reliable Code formatting [#4138](https://github.com/eclipse/che/issues/4138)

## Redesigned User Experience
- [ ] New IDE design and experience [#4929](https://github.com/eclipse/che/issues/4929), [#4993](https://github.com/eclipse/che/issues/4993)
- [ ] UD re-design for ws create + details + crane along with reducing output of agent boot [#4359](https://github.com/eclipse/che/issues/4359)
- [ ] Git integration as panel [#5128](https://github.com/eclipse/che/issues/5128)

## Infrastructure and Foundations
- [ ] Workspace Infrastructure (SPI) to support Docker and Openshift [#4736](https://github.com/eclipse/che/issues/4736)
- [ ] Client-Master communication [#5144](https://github.com/eclipse/che/issues/5144)
- [ ] _(best effort)_ GWT Super dev mode support [#1655](https://github.com/eclipse/che/issues/1655), [#2595](https://github.com/eclipse/che/issues/2595)


# April 2017 Update (Covering April - October)
## Users: Create a Professional Development Tool
Eclipse Che should provide a development experience that rivals world-class tools such as the Eclipse IDE and JetBrains. Che should install anywhere. Workspaces should be configurable to work with any kind of language and have best-in-class support for the language server protocol along with packaging all known language servers. Workspaces should be support Docker Compose and enable multi-machine development. There should be an intelligent commands framework that simplifies authoring commands and executing them on different machine targets.
- [ ] Performance of IDE as seen by the user [#3792](https://github.com/eclipse/che/issues/3792), [#4250](https://github.com/eclipse/che/issues/4250)
- [ ] Critical issues as documented by dev 
- [ ] LSP advancements - phase II + file extensions [#2109](https://github.com/eclipse/che/issues/2109)
- [ ] Debugger, debugger, debugger [#2611](https://github.com/eclipse/che/issues/2611)
- [ ] JavaScript IDE client prototype
- [ ] Improve Git commit window [#3614](https://github.com/eclipse/che/issues/3614)

## Enterprises: Cloud Dev for Teams on a Single Project
When enterprises adopt Eclipse Che (or the Codenvy derivative), they break themselves into teams that work on projects collectively, but in workspaces that are private and independent. Enterprises are looking to secure workspaces, deploy them on new infrastructure, and make it easier for teams to collaborate on projects together while maintaining developer autonomy. Some of these issues are Codenvy or Red Hat OpenShift issues, but generate significant improvements to the underlying Che platform.
- [ ] System stack + template + factory + recipes mgmt [#1902](https://github.com/codenvy/codenvy/issues/1902), [#]()
- [x] Traffic through a single port [#4361](https://github.com/eclipse/che/issues/4361)
- [ ] Consolidate chefiles + factory JSON [#4362](https://github.com/eclipse/che/issues/4362)
- [x] Factory and PR panel in che [#4290](https://github.com/eclipse/che/issues/4290)
- [ ] Che and Codenvy infrastructure deploy on Kube / OpenShift [#2847](https://github.com/eclipse/che/issues/2847), [#5052](https://github.com/eclipse/che/pull/5052)
- [ ] Simplified IDE UI
- [x] Improvements for terminals [#4824](https://github.com/eclipse/che/issues/4824)
- [ ] UD re-design for ws create + details + crane along with reducing output of agent boot [#4359](https://github.com/eclipse/che/issues/4359)
 
## Ecosystem: Make It Easy to Contribute to Che
Eclipse Che should be easy to customize. Che has many customization points including stacks, templates, extensions, plugins, assemblies, and commands. Currently, these customization and extension points are located and customized in differnet ways. We are going to centralize and standardize these items to make a consistent model for how customizers can work with Che. Additionally, we will advance the infrastructure of Che and our DevOps infrastructure to make it possible to duplicate Che development environments for those that want to give back to the project.
- [x] Archetype SDK (lifecycle of custom assemblies) [#4257](https://github.com/eclipse/che/issues/4257) & [archetype](https://github.com/eclipse/che-archetypes/issues) 
- [ ] QE automation framework [TBD] 
- [ ] Custom images for each branch with auto-generation from CI [TBD] 
- [x] Agent & Machine refactoring [#3971](https://github.com/eclipse/che/issues/3971) & [#3612](https://github.com/eclipse/che/issues/3612) 
- [ ] Improved Eclipse Che extensions development flow [#4370](https://github.com/eclipse/che/issues/4370)
- [ ] Che-in-Che development model with ability to source workspace recipe from git repo 
- [ ] Various internal refactoring [#3244](https://github.com/eclipse/che/issues/3244), [#3248](https://github.com/eclipse/che/issues/3248), [#4221](https://github.com/eclipse/che/issues/4221)
- [ ] Rework agents installation [#3971](https://github.com/eclipse/che/issues/3971)
- [ ] Use a single port to route all traffic [#4361](https://github.com/eclipse/che/issues/4361)
- [ ] Replace everrest based Websocket calls with new RPC framework. [#4459](https://github.com/eclipse/che/issues/4459)

# September 2016
## Users: Create a Professional Development Tool
Eclipse Che should install anywhere and be easy to install. It should also be possible for you to get a project-typed workspace with a custom set of commands in a natural, minimal sequence. Eclipse Che should become context-aware and auto-generate workspaces with type and code information based upon the contents of directory or repository.
- [x] Make docker the default execution for Che. [#1683](https://github.com/eclipse/che/pull/1683)
- [x] Add support for the Codenvy / Red Hat / Microsoft language server protocol [#1287](https://github.com/eclipse/che/issues/1287)
- [x] "Code in Che" from any git repository [#1895](https://github.com/eclipse/che/issues/1895)
- [x] Second phase of "Code in Che" from any git repository [#2266](#2266)
- [x] Simplify dashboard navigation to eliminate unnecessary clicks [#1743](https://github.com/eclipse/che/issues/1743) 
- [x] Move dashboard navigation to list layout [#1762](https://github.com/eclipse/che/issues/1762)
- [x] Move workspace editing to form layout [#1767](https://github.com/eclipse/che/issues/1767)
- [x] Support `/namespace/workspace` URL access [#1572](https://github.com/eclipse/che/pull/1572)
- [x] Split view for editor [#1837](https://github.com/eclipse/che/issues/1837)
- [ ] Make it possible to add / remove servers without customizing a Dockerfile
- [ ] Provide image project type to simplify edit, build, debug of images
- [x] Ability to preview HTML files [#1883](https://github.com/eclipse/che/issues/1883)
- [x] Add intelligent commands - executing against a context [#2681](https://github.com/eclipse/che/issues/2681)

## Customizers: Make Customizations More Approachable
Eclipse Che should be easy to customize. Che has many customization points including stacks, templates, extensions, plugins, assemblies, and commands. Where possible, we should make these customizations happen within Che's dashboard or as a project type within the IDE. For assembly-related items, such as custom stacks, Che should be self-updating and dynamic for the addition and removal of items. For extension-related items, such as the IDE, Che should have a simple way to get started developing plug-ins with incremental builds and, if necessary, super dev modes. The project must also evolve its interfaces to support community projects to create value-added layers within Che such as ecore, EMF, GMF, and multi-cursor editing.

- [x] Add, edit, and delete templates and stacks from the dashboard [epic:2205](#2205)
- [ ] Localhost machines, to create workspaces without Docker on the host
- [x] Simpler Che-in-Che scenarios [epic:2116](https://github.com/eclipse/che/issues/2116)
- [x] Provide docker images for building Che to reduce configuration [See wiki](https://github.com/eclipse/che/wiki/Development-Workflow#build-che-using-docker)
- [x] Dynamic file watchers with events to auto-update IDEs when workspace files are edited out of band [#1824](https://github.com/eclipse/che/issues/1824)
- [x] JPA data access implementation to store information with in-memory databases [#1790](https://github.com/eclipse/che/issues/1790)
- [x] Make it easier for third party tools to integrate Che [#1894](https://github.com/eclipse/che/issues/1894)
- [x] Refactor che-server and che-launcher containers to use single volume mount for data bindings [#2786](https://github.com/eclipse/che/pull/2786)
- [x] Add initial support for Chedir, reproducible dev environments [#1895](https://github.com/eclipse/che/issues/1895)
- [x] Add support for Chefile interoperability with Factories, and automatic configuration of SSH keys [#2266](https://github.com/eclipse/che/issues/2266)

## Enterprises: Expand Che Execution Scenarios
Che needs to run in a variety of environments and support large-scale workspace consumption in an elastic way. There needs to be a clear, prescriptive set of controls for admins who adminster Che systems. We will enable multi-node elasticity in Che, and we will defer multi-user, multi-tenant, and organizational implementations to commercial vendors building more advanced versions of Che.
- [x] Allow off-the-shelf docker images to work within Che [#1823](https://github.com/eclipse/che/issues/1823)
- [x] Dynamic injection of workspace agents [#1823](https://github.com/eclipse/che/issues/1823)
- [x] Start a new workspace with a Docker compose definition - part of 5.0.0-M1 release
- [x] Switch between different runtime environments in a single workspace
- [ ] Environment SPI, to allow platform providers like OpenShift to create plugins to manage workspace runtimes [#1829](https://github.com/eclipse/che/issues/1829)
- [ ] Che with a reverse proxy to minimize port exposure (workspace URLs will be embedded) [#1560](https://github.com/eclipse/che/issues/1560)
- [x] Migrate Docker images from Codenvy into the eclipse/ DockerHub organization[#2737](https://github.com/eclipse/che/issues/2737)
- [x] Create Che machine exec concept to solve issues with Docker exec [#1944](https://github.com/eclipse/che/issues/1944)