For past milestones, see the [Changelog](https://github.com/eclipse/che/blob/master/CHANGELOG.md).

As part of our 6-9 month roadmap, we are restructuring the underlying workspace model to support workspaces with multiple machines, dynamically deployed agents to make base images lighter, virtual file system so editors and IDEs can be notified of changes made by other clients, a new Chefile capability which provides a Vagrant-style workflow for Che workspaces, and consolidated support for an underlying database model.

##5.2.0 (latest)
_Milestone Details:_ https://github.com/eclipse/che/issues/3976

_Primary Goals_

- Docker Compose Support in Chefiles: Multi-machine workspaces automatically generated from your repo.
- Multi-Che Support: Easily run multiple Che instances on the same host.
- File-Context Git Actions: File context menu for common git actions.
- PHP Composer: Support for the popular PHP scaffolding utility.
- Updated PHP Tutorial: Try all the new PHP intellisense and debugging.
- Memory & Disk Checks on Startup: Resource checks when starting Che.
- Networking Checks on Startup: Checks browser to workspace and server to workspace connectivity to avoid common network issues.
- Improved CLI Output: More detail has been added to the info command plus you can generate a diagnostic snapshot for problems.
- CPU Limiting for Docker Builds: Docker builds can be CPU intensive so they now carry CPU limits to prevent starving other workspaces.
- Restart a Failed Workspace: You can now easily restart workspaces that didn’t start correctly the first time.
- Python Intellisense: Syntax highlighting and hover-over help docs.

##5.1.0 
_Milestone Details:_ https://github.com/eclipse/che/issues/3972

_Note:_ Major release.

_Primary Goals_
> * Many new features provided.

- New CLI: Offline installation, simple configuration, and data backup.
- BitBucket Server Integrations: Connect to JIRA, Jenkins and automate pull requests with BitBucket repos.
- Consolidate Databases: Because a single database is easier to manage.
- Built-in Documentation: {your-codenvy-url}/docs to get help.
- Docker Compose Runtimes: Dev workspaces with multiple containers.
- Workspace Snapshots: Auto-image and auto-restore workspace state
- Workspace Agents: Inject developer services into any workspaces.
- Docker Exec Agent: Replaces docker exec with Golang REST server for executing commands.
- Stack Editor: Create stacks with your runtime, or edit and test any of our 30+ default stacks.
- Language Server Protocol: Add intellisense for any language.
- New Debuggers: Added new Node.JS and Zend PHP debuggers.
- SSH: Automatic key generation across all machines in a workspace.
- Desktop Sync: Synchronize workspaces with your local IDE.
- More Responsive: Filesystem watchers optimize file operations and browser updates.
- Split & Resize: Terminals and editors can be split and sized to your exacting requirements.
- PHP: Auto-complete, definitions, debugging and more.
- Bitnami Stacks: Certified workspace stacks for popular languages and frameworks.
- Chedir: Reproducible cloud workspaces from your local repo.

##5.0.1 
_Milestone Details:_ https://github.com/eclipse/che/issues?q=is%3Aissue+milestone%3A5.0.1+is%3Aclosed

_Note:_ Hot bug fix release.

_Primary Goals_
> * Hot bug fixes.

##5.0.0  
_Milestone Details:_ https://github.com/eclipse/che/issues/3093

_Note:_ This is a GA milestone in the new 5.0 stream. There are model changes in Che 5 that make the milestone builds incompatible with the workspaces of 4.x - see the Milestone Details for more information.

_Primary Goals_
> * GA ready.

##5.0.0-M9
_Milestone Details:_ https://github.com/eclipse/che/issues?q=is%3Aissue+milestone%3A5.0.0+is%3Aclosed

_Note:_ This is a pre-GA milestone in the new 5.0 stream. There are model changes in Che 5 that make the milestone builds incompatible with the workspaces of 4.x - see the Milestone Details for more information.

##5.0.0-M8
_Milestone Details:_ https://github.com/eclipse/che/issues/3094

_Note:_ This is a pre-GA milestone in the new 5.0 stream. There are model changes in Che 5 that make the milestone builds incompatible with the workspaces of 4.x - see the Milestone Details for more information.

_Primary Goals_
> * Create and edit workspace using raw config
> * REST method improvements for Projects
> * Improved highlight in project explorer
> * Use OpenJDK in che-server
> * Updated .NET Core Template
 
##5.0.0-M7 
_Milestone Details:_ https://github.com/eclipse/che/issues/2935

_Note:_ This is a pre-GA milestone in the new 5.0 stream. There are model changes in Che 5 that make the milestone builds incompatible with the workspaces of 4.x - see the Milestone Details for more information.

_Primary Goals_
> * Visual stack editor
> * SSH improvements
> * Improved Che mount container utility
> * Compose improvements
> * Clarified snapshotting language

##5.0.0-M6
_Milestone Details:_ https://github.com/eclipse/che/issues/2740

_Note:_ This is a pre-GA milestone in the new 5.0 stream. There are model changes in Che 5 that make the milestone builds incompatible with the workspaces of 4.x - see the Milestone Details for more information.

_Primary Goals_
> * Bug fixes

##5.0.0-M5
_Milestone Details:_ https://github.com/eclipse/che/issues/2359

_Note:_ This is a pre-GA milestone in the new 5.0 stream. There are model changes in Che 5 that make the milestone builds incompatible with the workspaces of 4.x - see the Milestone Details for more information.

_Primary Goals_
> Node.js debugging with GDB
> Improvments to stack editing
> PHP project type improvements
> Bug fixes

##5.0.0-M4
_Milestone Details:_ https://github.com/eclipse/che/issues/2615

_Note:_ This is a pre-GA milestone in the new 5.0 stream. There are model changes in Che 5 that make the milestone builds incompatible with the workspaces of 4.x - see the Milestone Details for more information.

_Primary Goals_
> * Bug fixes

##5.0.0-M3
_Milestone Details:_ https://github.com/eclipse/che/issues/2641

_Note:_ This is a pre-GA milestone in the new 5.0 stream. There are model changes in Che 5 that make the milestone builds incompatible with the workspaces of 4.x - see the Milestone Details for more information.

_Primary Goals_
> * New stack editor in the user dashboard
> * Expanded workspace configuration in the dashboard
> * Smoothing and simplifying of the user interface
> * Support for the Codenvy/Microsoft/RedHat language server protocol standard
> * Upgrade to Orion 12
> * Consolidated database

##5.0.0-M2
_Milestone Details:_ https://github.com/eclipse/che/issues/2640

_Note:_ This is a pre-GA milestone in the new 5.0 stream. There are model changes in Che 5 that make the milestone builds incompatible with the workspaces of 4.x - see the Milestone Details for more information.

_Primary Goals_
> * Bug fixes


##5.0.0-M1
_Milestone Details:_ https://github.com/eclipse/che/issues/2267

_Note:_ This is a pre-GA milestone in the new 5.0 stream. There are model changes in Che 5 that make the milestone builds incompatible with the workspaces of 4.x - see the Milestone Details for more information.

_Primary Goals_
> * Multi-machine workspaces with YAML syntax
> * Workspace agents to allow any Docker image to work in Che without additional syntax
> * Gitlab integration
> * Che launcher profiles to simplify managing multiple Che configurations on the same machine

##4.7.2
_Milestone Details:_ https://github.com/eclipse/che/issues/2401

_Primary Goals_
> * Bug fixes

##4.7.1
_Milestone Details:_ https://github.com/eclipse/che/issues/2354

_Primary Goals_
> * Add Bitnami Express 4.13.4 stack and blank project for use with express-generator #2301
> * Bug fixes

##4.7.0
_Milestone Details:_ https://github.com/eclipse/che/issues/2029

_Primary Goals_
> * Configuration for using Docker and Docker Compose inside Che workspaces
> * Che CLI with profiles to quickly run multiple Che configurations
> * New command macros 

##4.6.0
_Milestone Details:_ https://github.com/eclipse/che/issues/1870

_Primary Goals_
> * New docker image launcher for Che
> * New lighter image for Che based upon alpine

##4.5.0
_Primary Goals_
> * Ability to add / remove / update stacks + templates from within Dashboard
> * Ability for user to change RAM for workspace within Dashboard
> * Usability cleanup of the tables in Dashboard 
> * (maybe) simple UI improvements to the IDE to soften some of the colors and reduce the black lines

##4.4.0
_Primary Goals_
> * Ability to connect and use private Docker registry
> * New left navigation bar for Dashboard and IDE

##4.3.0
_Primary Goals_
> * New Maven Plug-in, Classpath Configuration and Java Project Type
> * SVN Plug-in
> * UX Improvements: Nofifications, Debugger, Dashboard and Consoles
> * Editor Personalization
> * Optimized Local Workspace Snapshots
> * Improved Vagrant Installer
> * Generic Debugger API

## 4.2.0
_Primary Goals_
> * New runtime stacks, templates, and commands for C, C++, Python and Android
> * GDB debugger for C, C++, Python and many other languages
> * Remote development of devices over SSH
> * Workspace auto-snapshot flows
> * New Vagrant-based installer

## 4.1.0
_Primary Goals_
> * Provide a new maven plug-in that has an internal model of the entire maven configuration structure. This enables advanced capabilities around classpath construction and global POM definitions.
> * Remote machines with command execution on remote targets.
> * C/C++ Plugin, templates, and all-in-one stack
> * Add debugger support for gdbserver, which adds over 15 languages including Go, C/C++

## 4.0.0
_Primary Goals_
> * Implementation of a workspace server which provide developer workspaces composed of projects and environments. Environments are composed of machines powered by Docker. Workspaces configuration are persisted and portable.

> * New cloud IDE with advanced Java Features and new UI/UX.

> * New user dashboard to manage user's workspaces.

**New Workspace Server**
* Environments with Docker-based machine
* Projects injection
* Workspace lifecycle management
* RESTful access
* SSH/Terminal access
* Portability with shared access
* Commands injection support

**Cloud IDE**
* Use Orion as text editor
* Remote Java Debugger
* Devops perspective
* New console and terminal panel
* Full text search
* Git diff viewer

**Java Features**
* Java 8 support
* Use JDT for Java projects
* Refactoring: class, packages, attributes, methods
* Navigation: class structure, jump to definition
* Multi-module support
* Move classes, packages
* Quick fixes
* Code completion
* Quick documentation

**Dashboard**
* Manage workspaces
* Manage projects
* Guided flow to create projects and workspaces

**Others**
* Set of ready-to-use stacks
* Set of samples projects
