# Eclipse Che Roadmap
Eclipse Che follows a release cycles with a sprint planned every 3 weeks, with a collection of 4 sprints combining to a major release every 3 months. While working on a current sprint, we plan the following sprint. We thematically break the major functionality into epics that have sub-issues that can span many sprints, and sometimes across many releases. We do our best to incorporate all of a feature into a single release, but it often requires that we break functionality across multiple release milestones.

Sprints are numbered, while major releases (or trains) are named after flowers, in alphabetical order. The current sprint is sprint #149, which started on 2018-05-09 and will finish on 2018-05-29. It is the 2nd sprint in the Iris release train.

The epics and features that roll into a milestone are determined by pull request readiness of the feature at the time a milestone begins. In other words, we only place into a milestone features that are code complete and waiting for master-integration and testing.

# Current sprint planning

At any time you can see what is being worked on:
- See [high level planning per sprint per team](https://github.com/eclipse/che/labels/kind%2Fplanning)
- See [issues in the current sprint](https://github.com/eclipse/che/labels/sprint%2Fcurrent-sprint).
- See [issues planned for the following sprint](https://github.com/eclipse/che/labels/sprint%2Fnext-sprint).
- See [PRs in code-review](https://github.com/eclipse/che/pulls?q=is%3Apr+is%3Aopen+label%3Astatus%2Fcode-review).


# Themes for 2018
- Plugins: Features to drive further growth in the Che ecosystem.
- IDE.next: Updates to the IDE to increase the joy of development.
- Workspace.next: Improvements to workspace creation and tool interaction to improve the fidelity between developer workspace and production environment. 
- Enterprises: Features to support large scale use of Che
[//]: # I would like to add release calendar also (number & name of current release, last few releases, with links to release notes)

## Plugins
Eclipse Che is a platform to build cloud-native tools. For Che to be successful on this goal, it requires a strong extensibility model with an enjoyable contributor developer experience. 

In the past, Eclipse Che's extensibility was focused on white labelling use cases. ISV were able to customize Eclipse Che, build their own version by completely customizing it and distributing it to their own audiences. While that extensibility approach has been great for many partners, it has always been seen as complex, with a technology stack (especially GWT in the IDE) which resulted in a non-optimal developer experience. The lack of a dynamic extensibility also forced a Che Plugin to be packaged in a "Che assembly" in order to make it available to the end-users. There was no way to quickly build a plugin, package it so that it could be installed in a running Che and make it available without rebuilding all of Che. 

To address these issues we'll be phasing out the GWT-based IDE in favour of another open Eclipse Foundation IDE project: [Theia](https://github.com/theia-ide/theia). This new IDE is built using TypeScript and has the foundations which will allow us to build a more flexible, easier to use and faster to deploy plugin experience.

Our main goal is to provide a dynamic plugin model. In Che, a user shouldn't need to worry about the dependencies needed for the tools running in their workspace - they should just be available when needed. This means that a Che plugin will provide its dependencies and its "back-end" services (which could be running in a sidecar container connected to the user's workspace) and the IDE UI extension. Packaging all these elements together we can ensure that the user's impression is that Che "magically" was able to provide language services and developer tooling they need for their workspace.

In order to expose these plugins and make them consumable we will build a Che plugin marketplace. This will be open to the community, but also allow private Che installs behind firewalls to create their own in-house marketplace with only those plugins which are appropriate for their use made available.

#### Plugin Model
- [ ] Plugin system for Theia, with dynamic extensibility [#1482](https://github.com/theia-ide/theia/issues/1482)
- [ ] Authentication and security for Che plugins [#9383](https://github.com/eclipse/che/issues/9383)

#### Contributor Developer Experience
- [ ] Self Hosting [#8267](https://github.com/eclipse/che/issues/8267)

#### Marketplace
- [ ] Che Plugin Marketplace - Phase 1 [#8282](https://github.com/eclipse/che/issues/8282)


## IDE.next
We have decided to integrate [Theia](https://github.com/theia-ide/theia) into Che to replace our GWT based IDE because it offers simpler extensibility and has many of the foundations we feel will be needed going forward. However, there is a  substantial feature gap between Theia and our current Che IDE. Much of this year will be spent adding needed features to Theia so that it can fully replace the current IDE. During this time we will be doing minimal work on the GWT-based Che IDE.

#### Language 
- [ ] Switch Java infrastructure to JDT LS in Che 6 [#6157](https://github.com/eclipse/che/issues/6157)
- [ ] Multiroot Support in Che 6 [#9486](https://github.com/eclipse/che/issues/9486)
- [ ] LSP feature gap with Theia [#8514](https://github.com/eclipse/che/issues/8514)
- [ ] LS running in sidecars [#9441](https://github.com/eclipse/che/issues/9441)

#### Debugger
- [ ] Support Debug Adapter Protocol [#8303](https://github.com/eclipse/che/issues/8383), [#1573](https://github.com/theia-ide/theia/issues/1573)
- [ ] Provide NodeJS Debugger
- [ ] Provide Java Debugger
- [ ] Multi-containers and remote debugging [#8809](https://github.com/eclipse/che/issues/8809)

#### Commands & Tasks
- [ ] Commands support with Theia [#8382](https://github.com/eclipse/che/issues/8382), [#1698](https://github.com/theia-ide/theia/issues/1698), [#8974](https://github.com/eclipse/che/issues/8974)
- [ ] Commands API for Workspace.Next [#9546](https://github.com/eclipse/che/issues/9546)

#### Testing 
- [ ] Generic Testing Support [#5978](https://github.com/eclipse/che/issues/5978)

#### Terminal
- [ ] Terminal to access any workspace's container with Theia [#8698](https://github.com/eclipse/che/issues/8698), [#1](https://github.com/eclipse/che-theia-terminal-plugin/pull/1)

#### Live Collaborations
- [ ] Live collaboration capabilities [#8286](https://github.com/eclipse/che/issues/8286)

#### Other Cool Stuffs
- [ ] Basic support for tablets [#6527](https://github.com/eclipse/che/issues/6527)
- [ ] Presentation Mode [#6187](https://github.com/eclipse/che/issues/6187)
- [ ] Guided Flows and Tutorials in Che [#6150](https://github.com/eclipse/che/issues/6150)

## Workspace.next
Eclipse Che developers all start with a container image. In most cases this should be the same image that is used in production. Today to add the developer tooling needed (which won't be in a production image), Che injects language servers, SSH and terminal access into the container. This makes it easy for the developer, but it alters the container so that it is no longer an exact replica of what's running in production. There is a better way.

Changes will be made so that the workspace tooling is microservice-packaged and isolated from the developer's workspace image and from each other. Each tool plugin the developer needs can be deployed as its own container and connected to the developer's workspace (we call this a "side car" container). These side car tools will have their own lifecycle with the ability for easy upgrade and their own scalability mechanisms.

The workspace model is also going to be improved to better leverage a Kubernetes-friendly application stack definition (kubernetes.yaml, Helm Chart). The workspace engine will be capable of interpreting an application stack definition and generating the Che workspace needed to code on that application.

Finally, we will be investing in support of [ISTIO](https://istio.io/) and Serverless functions (via [OpenWhisk](https://openwhisk.apache.org/) for example).

#### Foundations
- [x] Run Theia in a sidecar container
- [ ] Workspace.Next [#8265](https://github.com/eclipse/che/issues/8265)
- [ ] Workspace.Next phase 1 [#9406](https://github.com/eclipse/che/issues/9406)

#### Preferences
- [ ] Preferences system at workspace level and system level [#9336](https://github.com/eclipse/che/issues/9336)

#### Cloud Technologies
- [ ] Development support for applications using ISTIO [#6957](https://github.com/eclipse/che/issues/6957)


## Enterprises
Eclipse Che has gained a great deal of interest in large enterprises who are moving to containers and looking for a way to standardize the developer workspace and removing source IP from hard-to-secure laptops. However, there are a number of features needed in order to make Che a simple-to-manage tool for these large and (often) private environments. Organizations are looking to secure workspaces, deploy them on new infrastructure, and make it easier for teams to collaborate on projects together while maintaining developer autonomy. Maintenance and Ops should be facilitated.

#### Infrastructure Support
- [x] Kubernetes Support [#1193](https://github.com/eclipse/che/issues/1193), [#5908](https://github.com/eclipse/che/issues/5908), [#7589](https://github.com/eclipse/che/issues/7589)
- [ ] Create OpenShift objects under current user account on OCP [#8178](https://github.com/eclipse/che/issues/8178)
- [ ] Che on OpenShift Online [#8729](https://github.com/eclipse/che/issues/8729)

#### Ops Features
- [ ] Update Che without restart [#8547](https://github.com/eclipse/che/issues/8547)

#### Infrastructure Support
- [x] Kubernetes Support [#1193](https://github.com/eclipse/che/issues/1193), [#5908](https://github.com/eclipse/che/issues/5908), [#7589](https://github.com/eclipse/che/issues/7589)

#### Telemetry
- [ ] Generic telemetry events infrastructure [#5483](https://github.com/eclipse/che/issues/5483) 


# Past Releases

| Sprint start | Sprint end | Sprint number | Release train |
|---------------|---------------|-------|-------------------|
| 9-Aug-2017	| 29-Aug-2017	| 136	| Freesia 1 |
| 30-Aug-2017	| 19-Sep-2017	| 137	| Freesia 2 |
| 20-Sep-2017	| 10-Oct-2017	| 138	| Freesia 3 |
| 11-Oct-2017	| 31-Oct-2017	| 139	| Freesia 4 |
| 1-Nov-2017	| 21-Nov-2017	| 140	| Ginger 1  |
| 22-Nov-2017	| 12-Dec-2017	| 141	| Ginger 2  |
| 13-Dec-2017	| 2-Jan-2018	| 142	| Ginger 3  |
| 3-Jan-2018	| 23-Jan-2018	| 143	| Ginger 4  |
| 24-Jan-2018	| 13-Feb-2018	| 144	| Heather 1 |
| 14-Feb-2018	| 6-Mar-2018	| 145	| Heather 2 |
| 7-Mar-2018	| 27-Mar-2018	| 146	| Heather 3 |
| 28-Mar-2018	| 17-Apr-2018	| 147	| Heather 4 |
| 18-Apr-2018	| 8-May-2018	| 148	| Iris 1    |
| 9-May-2018	| 29-May-2018	| **149** | Iris 2    |
| 30-May-2018	| 19-Jun-2018	| 150	| Iris 3    |
| 20-Jun-2018	| 10-Jul-2018	| 151	| Iris 4    |