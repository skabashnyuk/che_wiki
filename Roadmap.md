For past releases, see the [Changelog](https://github.com/eclipse/che/blob/master/CHANGELOG.md).

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


## 4.1.0

_Primary Goals_
> * Provide a new maven plug-in that has an internal model of the entire maven configuration structure. This enables advanced capabilities around classpath construction and global POM definitions.
> * Remote machines with command execution on remote targets.
> * C/C++ Plugin, templates, and all-in-one stack
> * Add debugger support for gdbserver, which adds over 15 languages including Go, C/C++

**Maven plug-in**
* Resolving modules for multi-modules projects
* resolve dependencies and available source jars
* Custom Maven command
* Improve classpath building for Maven multi-module projects
* Display effective POM
* Resolve imports with quick fix feature

**Remote machines**
* New SSH machine type
* Add "Edit targets..." concept to machine drop down
* Display multiple machines in processes panel
* Execute commands on remote machines with output streaming

## 4.2.0
_Primary Goals_
> * Subversion plug-in
> * New Java features
> * UX improvements on dashboard
> * Plugin resource center + development tutorials

##4.3.0
_Primary Goals_
> * Workspace portability
> * Bring Codenvy's permission + security APIs into Che
> * Bring Codenvy's factory APIs into Che
> * Console panel improvements for usability