For past milestones, see the [Changelog](https://github.com/eclipse/che/blob/master/CHANGELOG.md).

As part of our 6-9 month roadmap, we are restructuring the underlying workspace model to support workspaces with multiple machines, dynamically deployed agents to make base images lighter, virtual file system so editors and IDEs can be notified of changes made by other clients, a new Chefile capability which provides a Vagrant-style workflow for Che workspaces, and consolidated support for an underlying database model.

As part of this exercise, we will provide these capabilities into a single 5.0 release targeted for later 2016. We have now started on the milestone train for 5.0 and will continue with various ship-quality milestones until we are satisfied with the usability and can provide migration paths for 4.x workspaces.

##5.0.0-M8 (In-Progress)
_Milestone Details:_ https://github.com/eclipse/che/issues/2935

_Note:_ This is a pre-GA milestone in the new 5.0 stream. There are model changes in Che 5 that make the milestone builds incompatible with the workspaces of 4.x - see the Milestone Details for more information.

_Primary Goals_
> * 

##5.0.0-M7 (Latest)
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
