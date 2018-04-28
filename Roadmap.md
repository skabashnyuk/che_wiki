This roadmap is a 6-12 month high level overview of what we plan to include in Eclipse Che. 

This roadmap is thematically tied to three audiences: 
1. Users (developers) 
1. Ecosystem (development community, ISVs) 
1. Admins (enterprises / teams) 

Releases occur every three weeks. While working on a current release, we plan the following release. We thematically break the major functionality into epics that have sub-issues that can span many sprints, and sometimes across many releases. We do our best to incorporate all of feature into a single release, but it often requires that we break functionality across multiple release milestones.

The epics and features that roll into a milestone are determined by pull request readiness of the feature at the time a milestone begins. In other words, we only place into a milestone features that are code complete and waiting for master-integration and testing.

## 2018 Roadmap - At a glance

The goals are decomposed into the following three themes:
- Ecosystem
- Support more Cloud Native technologies
- Pleasurable Development Tool

**Ecosystem**  
Eclipse Che is a platform to build cloud-native tools. For Che to be successful on this goal, it requires a strong extensibility model with a enjoyable contributor developer experience. 

In the past, Eclipse Che's extensibility has mainly been focused on the white labelling use cases. ISV were able to customize Eclipse Che, build their own version by completely customizing it and distributing it on their own. While that extensibility approach has been great for many partners, it has always been seen as complex, with a technology stack which was also relying an non-optimal developer experience with slow turnarounds. The lack of a dynamic extensibility approach also forced a Che Plugin to be packaged in the "Che assembly" in order to get available to the end-user. There was no way to build a plugin, package it so that it can be installed in a running Che (without having to rebuild a new Che). 

Moving forward on those different aspects, beginning of 2018 we decided to progressively get ride of the GWT-based IDE from Che to another IDE built by the community: [Theia](https://github.com/theia-ide/theia). This new IDE, is built using TypeScript and have some basics which will allow to build a really pleasurable extensible platform.

Most of the efforts on this area will be to provide a dynamic plugin model. In Che, a user must not worry about the dependencies needed for the tools running in a workspace. There should be nothing to install or configure - compared to traditional IDEs. A plugin will provide its dependencies and its "back-end" services (which could be running in its own sidecar container) and the IDE UI extension.

Along with this work, we will also build a plugin marketplace - which will have a public/community and in-house deployment capabilities.

**Support Cloud Native technologies**  
Developers using Eclipse Che use containers directly in their developer workspaces. The Che workspaces provide a "dev mode" on containers used onto production, adding intellisense and IDE tooling. 

The workspace model is going to be improved to better leverage an application stack definition (kubernetes.yaml, Helm Chart). IDE tooling will be microservices packaded in their own sidecar containers bringing their own dependencies and keeping application's containers "untouched". The execution of IDE tooling will be isolated from each other and from application's containers too. Each IDE tooling (and by extension plugin) will get its own lifecycle, ability for easy upgrade/switch and its own scalability mechanism.

Eclipse Che will get a workspace engine, capable of interpreting an application stack definition and generating the Che workspace needed to code on that application. 

We will also be investing efforts on supporting ISTIO and Serverless applications.

**Pleasurable Development Tool**  
While we decided to integrate [Theia](https://github.com/theia-ide/theia), there is a pretty substantial feature gap with the current GWT-based IDE provided within Che. Most of the efforts will be to fill the feature gap and leverage Che's contributor experience in Cloud IDE to bring [Theia](https://github.com/theia-ide/theia) to an acceptable level of maturity so it can replace the current IDE in Che. 

This will also give the opportunity to rethink and revamp some of the tools that we currently have and move the developer experience to a new pleasurable level. 


## Users: Professional and Pleasurable Development Tool
Eclipse Che should provide a development experience that rivals world-class tools such as the Eclipse IDE and JetBrains. Che should support any kind of language and have best-in-class support for the language server protocol and other server protocols. Workspaces should support development of multi-container applications. There should be an intelligent commands framework that simplifies authoring commands and executing them on different container targets. Preferences must provide two levels: workspace/system. Workspace must leverage application stack definitions and allow IDE tooling packaged as microservices running in sidecars.

### Foundations
- [x] Run Theia in a sidecar container
- [ ] Workspace.Next [#8265](https://github.com/eclipse/che/issues/8265)
- [ ] Workspace.Next phase 1 [#9406](https://github.com/eclipse/che/issues/9406)

### Language 
- [ ] Switch Java infrastructure to JDT LS in Che 6 [#6157](https://github.com/eclipse/che/issues/6157)
- [ ] Multiroot Support in Che 6 [#9486](https://github.com/eclipse/che/issues/9486)
- [ ] LSP feature gap with Theia [#8514](https://github.com/eclipse/che/issues/8514)
- [ ] LS running in sidecars [#9441](https://github.com/eclipse/che/issues/9441)

### Debugger
- [ ] Support Debug Adapter Protocol [#8303](https://github.com/eclipse/che/issues/8383), [#1573](https://github.com/theia-ide/theia/issues/1573)
- [ ] Provide NodeJS Debugger
- [ ] Provide Java Debugger
- [ ] Multi-containers and remote debugging [#8809](https://github.com/eclipse/che/issues/8809)

### Commands & Tasks
- [ ] Commands support with Theia [#8382](https://github.com/eclipse/che/issues/8382), [#1698](https://github.com/theia-ide/theia/issues/1698), [#8974](https://github.com/eclipse/che/issues/8974)
- [ ] Commands API for Workspace.Next [#9546](https://github.com/eclipse/che/issues/9546)

### Testing 
- [ ] Generic Testing Support [#5978](https://github.com/eclipse/che/issues/5978)

### Terminal
- [ ] Terminal to access any workspace's container with Theia [#8698](https://github.com/eclipse/che/issues/8698), [#1](https://github.com/eclipse/che-theia-terminal-plugin/pull/1)

### Preferences
- [ ] Preferences system at workspace level and system level [#9336](https://github.com/eclipse/che/issues/9336)

### Cloud Technologies
- [ ] Development support for applications using ISTIO [#6957](https://github.com/eclipse/che/issues/6957)

### Live Collaborations
- [ ] Live collaboration capabilities [#8286](https://github.com/eclipse/che/issues/8286)

### Other Cool Stuffs
- [ ] Basic suport for tablets [#6527](https://github.com/eclipse/che/issues/6527)
- [ ] Presentation Mode [#6187](https://github.com/eclipse/che/issues/6187)
- [ ] Guided Flows and Tutorials in Che [#6150](https://github.com/eclipse/che/issues/6150)


## Ecosystem: Make It Easy to Contribute to Che
Eclipse Che needs a dynamic plugin model. User should not have to install/configure anything to get a plugin in their workspaces. Plugins must communicate securely with Che Master. Che must provide a contributor experience which will allow to entirely build Che with Che and provide self hosting capabilities. A marketplace must emerge to let the contributors expose the plugins to the Che community.

### Plugin Model
- [ ] Plugin system for Theia, with dynamic extensibility [#1482](https://github.com/theia-ide/theia/issues/1482)
- [ ] Authentication and security for Che plugins [#9383](https://github.com/eclipse/che/issues/9383)

### Contributor Developer Experience
- [ ] Self Hosting [#8267](https://github.com/eclipse/che/issues/8267)

### Marketplace
- [ ] Che Plugin Marketplace - Phase 1 [#8282](https://github.com/eclipse/che/issues/8282)

## Enterprises: Cloud Dev for Enterprises and Teams 
When enterprises adopt Eclipse Che, they break themselves into teams that work on projects collectively, but in workspaces that are private and independent. Enterprises are looking to secure workspaces, deploy them on new infrastructure, and make it easier for teams to collaborate on projects together while maintaining developer autonomy. Maintenance and Ops should be facilitated.

### Infrastructure Support
- [x] Kubernetes Support [#1193](https://github.com/eclipse/che/issues/1193), [#5908](https://github.com/eclipse/che/issues/5908), [#7589](https://github.com/eclipse/che/issues/7589)
- [ ] Create OpenShift objects under current user account on OCP [#8178](https://github.com/eclipse/che/issues/8178)
- [ ] Che on OpenShift Online [#8729](https://github.com/eclipse/che/issues/8729)

### Ops Features
- [ ] Update Che without restart [#8547](https://github.com/eclipse/che/issues/8547)

### Infrastructure Support
- [x] Kubernetes Support [#1193](https://github.com/eclipse/che/issues/1193), [#5908](https://github.com/eclipse/che/issues/5908), [#7589](https://github.com/eclipse/che/issues/7589)

### Telemetry
- [ ] Generic telemety events infrastructure [#5483](https://github.com/eclipse/che/issues/5483) 


