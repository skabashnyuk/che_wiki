# Current and future releases
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
> * Better stability


## 4.2.0
_Primary Goals_
> * Better stability
> * SVN plug-in
> * Maven plug-in
> * New Java features
> * UX improvements on dashboard

**Maven plug-in**
* Resolving modules for multi-modules projects
* resolve dependencies and available source jars
* Custom Maven command
* Improve classpath building for Maven multi-module projects
* Ability to display effective POM
* Resolve imports with quick fix feature

**Others**
* Refactoring workspace environment model and project type
* API to copy files between machines
* Display name of currently used branch in editor

##4.3.0

_Primary Goals_
> * Better stability
> * New Java features
> * Strutural refactoring
> * Workspace portability improvements
> * Advanced Consoles panel

**Structural refactoring**
* Plug-ins to be splitted into two jars: one for the client, one for the server
* Split API between Che Workspace Master APIs, Che Workspace Agent APIs

**New Java features**
* Add type hierarchy view for Java
* Ability to setup format settings for Java code

**Workspace portability improvements**
* Workspace export with image snapshot
* Management of workspace snapshot in dashboard
* Workspace clone
* Save environment snapshot
* Ability to copy a workspace on cloud
* Restore workspace in latest state

**Advanced Consoles panel**
* Option to wrap-lines in outputs
* Syntax coloration in outputs
* Improved scrolling experience
* Ability to open a console in another browser tab
* Option to re-run a command

**Others**
* Improve SSH experience
* Support packages for Che to help the user to be properly setup
* Associate commands with stacks
* Shell syntax highlighting



# Past releases