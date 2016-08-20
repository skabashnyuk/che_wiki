For past milestones, see the [Changelog](https://github.com/eclipse/che/blob/master/CHANGELOG.md).

##4.7.0
_Primary Goals_
> * Che CLI with profiles to quickly run multiple Che configurations
> * API for VFS with file system watcher
> * Che stack and template
> * New command macros
> * Configuration for using Docker and Docker Compose inside Che workspaces
> * Full milestone details: https://github.com/eclipse/che/issues/2029

##4.6.0
_Primary Goals_
> * New docker image launcher for Che [#1683]
> * New lighter image for Che based upon alpine [#1682]
> * Full milestone details: https://github.com/eclipse/che/issues/1870

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
