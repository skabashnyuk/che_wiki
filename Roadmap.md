This roadmap acts as a 6-9 month forward-looking expectation of what we are working to incorporate into Eclipse Che. This roadmap is thematic tied to our three core audiences: a) users (developers), b) customizers (ISVs), and c) deployers (enterprises / teams). We schedule release milestones on a functionality basis with 2-3 milestones scheduled in advance. The length of a milestone is unknown, but we attempt to keep it less than a month and sometimes as short as 2 weeks. We map the epics implemented from the roadmap into each milestone. The epics and features that roll into a milestone are determined by pull request readiness of the feature at the time a milestone begins. In other words, we only place into a milestone features that are code complete and waiting for master-integration and testing.

## Users: Simplify the Getting Started Experience
Eclipse Che should install anywhere and be easy to install. It should also be possible for you to get a project-typed workspace with a custom set of commands in a natural, minimal sequence. Eclipse Che should become context-aware and auto-generate workspaces with type and code information based upon the contents of directory or repository.
- [ ] Make docker the default execution for Che. [#1683](http://github.com/eclipse/che/pulls/1683)
- [ ] "Code in Che" from any git repository
- [ ] Simplify dashboard navigation to eliminate unnecessary clicks
- [ ] Move dashboard navigation to list & form layouts
- [ ] Support `/namespace/workspace` URL access
- [ ] Make it possible to add / remove servers without customizing a Dockerfile
- [ ] Dynamic file watchers with events to auto-update IDEs when workspace files are edited out of band
- [ ] Provide image project type to simplify edit, build, debug of images

## Customizers: Make Customizations More Approachable
Eclipse Che should be easy to customize. Che has many customization points including stacks, templates, extensions, plugins, assemblies, and commands. Where possible, we should make these customizations happen within Che's dashboard or as a project type within the IDE. For assembly-related items, such as custom stacks, Che should be self-updating and dynamic for the addition and removal of items. For extension-related items, such as the IDE, Che should have a simple way to get started developing plug-ins with incremental builds and, if necessary, super dev modes. The project must also evolve its interfaces to support community projects to create value-added layers within Che such as ecore, EMF, GMF, and multi-cursor editing.

- [ ] Add, edit, and delete templates and stacks from the dashboard
- [ ] Localhost machines, to create workspaces without Docker on the host
- [ ] Simpler Che-in-Che scenarios (build is great, but need to run with GWT super dev mode)

## Enterprises: Make Che Production Grade
Che needs to run in a variety of environments and support large-scale workspace consumption in an elastic way. There needs to be a clear, prescriptive set of controls for admins who adminster Che systems. We will enable multi-node elasticity in Che, and we will defer multi-user, multi-tenant, and organizational implementations to commercial vendors building more advanced versions of Che.
- [ ] Allow off-the-shelf docker images to work within Che
- [ ] Start a new workspace with a Docker compose definition
- [ ] Switch between different runtime environments in a single workspace
- [ ] Dynamic injection of workspace agents
- [ ] Environment SPI, to allow platform providers like OpenShift to create plugins to manage workspace containers
- [ ] Elastic, multi-node Che
- [ ] Che with a reverse proxy to minimize port exposure (workspace URLs will be embedded) 