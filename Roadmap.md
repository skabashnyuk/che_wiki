This roadmap is a high level overview of what we plan to include in Eclipse Che. 

This roadmap is thematically tied to three audiences: 
1. Users (developers) 
1. Ecosystem (development community, ISVs) 
1. Admins (enterprises / teams) 

Releases occur every three weeks. While working on a current release, we plan the following release. We thematically break the major functionality into epics that have sub-issues that can span many sprints, and sometimes across many releases. We do our best to incorporate all of feature into a single release, but it often requires that we break functionality across multiple release milestones.

The epics and features that roll into a milestone are determined by pull request readiness of the feature at the time a milestone begins. In other words, we only place into a milestone features that are code complete and waiting for master-integration and testing.

## 2018 Roadmap - At a Glance

There are three primary themes:
- Plugin features to drive further growth in the Che ecosystem
- Improvements to workspace creation and tool interaction 
- Updates to the IDE to increase the joy of development

**Plugins and Ecosystem**

Eclipse Che is a platform to build cloud-native tools. For Che to be successful on this goal, it requires a strong extensibility model with an enjoyable contributor developer experience. 

In the past, Eclipse Che's extensibility was focused on white labelling use cases. ISV were able to customize Eclipse Che, build their own version by completely customizing it and distributing it to their own audiences. While that extensibility approach has been great for many partners, it has always been seen as complex, with a technology stack (especially GWT in the IDE) which resulted in a non-optimal developer experience. The lack of a dynamic extensibility also forced a Che Plugin to be packaged in a "Che assembly" in order to make it available to the end-users. There was no way to quickly build a plugin, package it so that it could be installed in a running Che and make it available without rebuilding all of Che. 

To address these issues we'll be phasing out the GWT-based IDE in favour of another open Eclipse Foundation IDE project: [Theia](https://github.com/theia-ide/theia). This new IDE is built using TypeScript and has the foundations which will allow us to build a more flexible, easier to use and faster to deploy plugin experience.

Our main goal is to provide a dynamic plugin model. In Che, a user shouldn't need to worry about the dependencies needed for the tools running in their workspace - they should just be available when needed. This means that a Che plugin will provide its dependencies and its "back-end" services (which could be running in a sidecar container connected to the user's workspace) and the IDE UI extension. Packaging all these elements together we can ensure that the user's impression is that Che "magically" was able to provide language services and developer tooling they need for their workspace.

In order to expose these plugins and make them consumable we will build a Che plugin marketplace. This will be open to the community, but also allow private Che installs behind firewalls to create their own in-house marketplace with only those plugins which are appropriate for their use made available.

**Workspace Changes**  
Eclipse Che developers all start with a container image. In most cases this should be the same image that is used in production. Today to add the developer tooling needed (which won't be in a production image), Che injects language servers, SSH and terminal access into the container. This makes it easy for the developer, but it alters the container so that it is no longer an exact replica of what's running in production. There is a better way.

Changes will be made so that the workspace tooling is microservice-packaged and isolated from the developer's workspace image and from each other. Each tool plugin the developer needs can be deployed as its own container and connected to the developer's workspace (we call this a "side car" container). These side car tools will have their own lifecycle with the ability for easy upgrade and their own scalability mechanisms.

The workspace model is also going to be improved to better leverage a Kubernetes-friendly application stack definition (kubernetes.yaml, Helm Chart). The workspace engine will be capable of interpreting an application stack definition and generating the Che workspace needed to code on that application.

Finally, we will be investing in support of [ISTIO](https://istio.io/) and Serverless functions (via [OpenWhisk](https://openwhisk.apache.org/) for example).

**IDE Updates**  
We have decided to integrate [Theia](https://github.com/theia-ide/theia) into Che to replace our GWT based IDE because it offers simpler extensibility and has many of the foundations we feel will be needed going forward. However, there is a  substantial feature gap between Theia and our current Che IDE. Much of this year will be spent adding needed features to Theia so that it can fully replace the current IDE. During this time we will be doing minimal work on the GWT-based Che IDE.

## Roadmap Details
### IDE Changes
Eclipse Che should provide a development experience that rivals world-class tools such as the Eclipse IDE and JetBrains. Che should support any kind of language and have best-in-class support for the language server protocol and other server protocols. Workspaces should support development of multi-container applications. There should be an intelligent commands framework that simplifies authoring commands and executing them on different container targets. Preferences must provide two levels: workspace/system. Workspace must leverage application stack definitions and allow IDE tooling packaged as microservices running in sidecars.

#### Foundations
- [x] Run Theia in a sidecar container
- [ ] Workspace.Next [#8265](https://github.com/eclipse/che/issues/8265)
- [ ] Workspace.Next phase 1 [#9406](https://github.com/eclipse/che/issues/9406)

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

#### Preferences
- [ ] Preferences system at workspace level and system level [#9336](https://github.com/eclipse/che/issues/9336)

#### Cloud Technologies
- [ ] Development support for applications using ISTIO [#6957](https://github.com/eclipse/che/issues/6957)

#### Live Collaborations
- [ ] Live collaboration capabilities [#8286](https://github.com/eclipse/che/issues/8286)

#### Other Cool Stuffs
- [ ] Basic support for tablets [#6527](https://github.com/eclipse/che/issues/6527)
- [ ] Presentation Mode [#6187](https://github.com/eclipse/che/issues/6187)
- [ ] Guided Flows and Tutorials in Che [#6150](https://github.com/eclipse/che/issues/6150)


### Ecosystem: Make It Easy to Contribute to Che
Eclipse Che needs a dynamic plugin model. User should not have to install/configure anything to get a plugin in their workspaces. Plugins must communicate securely with Che Master. Che must provide a contributor experience which will allow to entirely build Che with Che and provide self hosting capabilities. A marketplace must emerge to let the contributors expose the plugins to the Che community.

#### Plugin Model
- [ ] Plugin system for Theia, with dynamic extensibility [#1482](https://github.com/theia-ide/theia/issues/1482)
- [ ] Authentication and security for Che plugins [#9383](https://github.com/eclipse/che/issues/9383)

#### Contributor Developer Experience
- [ ] Self Hosting [#8267](https://github.com/eclipse/che/issues/8267)

#### Marketplace
- [ ] Che Plugin Marketplace - Phase 1 [#8282](https://github.com/eclipse/che/issues/8282)

### Cloud Dev for Large and Teams 
When large teams (hundreds or thousands of developers) adopt Eclipse Che, they break themselves into teams that work on projects collectively, but in workspaces that are private and independent. Organizations are looking to secure workspaces, deploy them on new infrastructure, and make it easier for teams to collaborate on projects together while maintaining developer autonomy. Maintenance and Ops should be facilitated.

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


