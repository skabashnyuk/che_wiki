The best way to understand how a project works or to debug an issue is to get the source, built it, and run it locally. We document the best practices for developing improvements to the product. Eclipse Che has three major subsystems: the Che server, the agents running within a workspace, and the user dashboard (a JavaScript app). The workflow for each can be slightly different.

## Build and Run From Source
### Dependencies
* Docker 1.8+
* Maven 3.3.1+
* Oracle Java 1.8 -- compilation with openjdk is not yet supported

To build the Che core, you will need the maven-patch-plugin. Windows does not support this plugin, and we give instructions on how to skip this plugin when building.

To build the user dashboard submodule, you will need npm, bower, and gulp.

### Clone
```sh
git clone https://github.com/eclipse/che.git
```
If master is unstable, checkout the latest tagged version.

### Build and Run - Tomcat
In its purest form, Che runs as a Tomcat server.

```sh
cd che/assembly
mvn clean install

# A new assembly is placed in:
cd che/assembly/assembly-main/target/eclipse-che-<version>/eclipse-che-<version>

# Executable files are:
bin/che.sh
bin/che.bat
```
Che will be available at ```localhost:8080```.

### Build and Run - Docker
We distribute Eclipse Che as a Docker image and this is the preferred way for users to install and run Che. You can use our Che images that run your local Che binaries, or you can create a new Docker image that contains your binaries.

```sh
# TODO: Link to page on how to mount local binaries to image
```
```sh
# TODO: Instructions on how to build Docker image from source
docker build -t che-server -f dockerfiles/che-server/Dockerfile .

# Now configure the che-launcher Docker image to use the Che image
# TODO: Instruction on how to modify the Dockerfile with right che-server reference
docker build -t che-launcher -f dockerfiles/che/Dockerfile .

# Now run Che
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock che-launcher start 
```

### Build Submodules
Building `/assembly` pulls already-built libraries for `/core`, `/plugins`, and `/dashboard` from our Nexus repository. You can build these submodules individually.

To build the core:
```sh
# Install maven-patch-plugin as an additional dependency.
cd che/core

# Windows: maven-patch-plugin does not work, so skip tests when building:
mvn -DskipTests=true -Dfindbugs.skip=true -Dskip-validate-sources clean install
```

To build plugins:
```sh
cd che/plugins
mvn clean install
```

To build the user dashboard:
```sh
# You need npm, bower, and gulp installed.
# See setup instructions in /dashboard
cd che/dashboard
mvn clean install
```

### Build Che Using Docker
If you want to avoid setting up the dependencies to build Che and its submodules, we provide a Docker image that has the dependencies necessary to build Che. You can mount Che source code from your host to the container and then compile the code within the container. Note - Docker I/O performance varies, and container compilation may be slower than native.

```sh
# For Mac + Linux:
docker run -it --rm --name build-che 
           -v "$HOME/.m2:/home/user/.m2" 
           -v "$PWD":/home/user/che-build 
           -w /home/user/che-build 
           codenvy/che-dev 
           mvn -DskipTests=true 
               -Dfindbugs.skip=true
               -Dgwt.compiler.localWorkers=2 -T 1C 
               -Dskip-validate-sources 
               clean install
               
# For Windows, replace $HOME with maven repo directory.
# For Windows, replace $PWD with Che source code directory.
```

## Validate Your Changes
We have integrated findbugs into the maven build system to generate warnings during the build. If your code generates new warnings or errors from findbugs, you must eliminate those issues before submitting the pull request. You can skip these checks by passing `-Dfindbugs.skip=true` to the maven build.

We have integrated [Error Prone](https://github.com/google/error-prone) to check the state of code when you execute a maven build. Error prone verification is required to pass for all code submissions.

License checks for submitted files are done within a maven build. You can skip these license checks with `-Dskip-validate-sources` maven option.
 
## Debugging

## Unit Testing
All functionality requires a unit test. Unit tests are executed as part of the build with `mvn clean install` for any module. When writing tests you can use JUnit or TestNG [with the Maven Surefire plugin](http://maven.apache.org/surefire/maven-surefire-plugin/examples/testng.html). If you want to run only unit tests on a module, execute `mvn clean test`.

## Linting


## Work Branches
Even if you have push rights on the eclipse/che repository, you should create a personal fork and create feature branches where you need them. We try to name the feature branch to match the GitHub issue that is being worked on. This keeps the main repository clean and your personal workflow cruft out of sight.

## Pull Requests
Before we can accept a pull request from you, you'll need to sign a [Contributor License Agreement (CLA)](https://github.com/eclipse/che/wiki/Contributor-License-Agreement). It is an automated process and you only need to do it once.

To enable us to quickly review and accept your pull requests, always create one pull request per issue and link the issue in the pull request. Never merge multiple requests in one unless they have the same root cause. Be sure to follow our coding guidelines and keep code changes as small as possible. Pull requests should contain tests whenever possible.

### 
Check out the [full issues list](http://github.com/eclipse/che/issues) for a list of all potential areas for contributions. Note that just because an issue exists in the repository does not mean we will accept a contribution to the core editor for it. There are several reasons we may not accepts a pull request like:

- Performance - One of Che's core values is to deliver a localhost-equivalent distributed workspace server. This means that workspaces must perform well in both real and perceived performance.
- User experience - Since we want to deliver a minimalist IDE, the UX should feel small and simple to navigate. We want to avoid cluttering. Most changes to the UI need to be approved by the UX team.
- Architectural - The team and/or feature owner needs to agree with any architectural impact a change may make. Things like new extension APIs must be discussed with and agreed upon by the feature owner.

To improve the chances to get a pull request merged you should select an issue that is labeled with the help-wanted or bug labels. If the issue you want to work is not labeled with help-wanted or bug, you can start a conversation with the issue owner asking whether an external contribution will be considered.

## Etiquette
In order to keep the conversation clear and transparent, please limit discussion to English and keep things on topic with the issue. Be considerate to others and try to be courteous and professional at all times. Everyone participating in the project must follow the [Eclipse Community Code of Conduct](https://www.eclipse.org/org/documents/Community_Code_of_Conduct.php).

## Repository Layout
### Modules
Our repository is broken in a variety of independently buildable submodules.
```
/che
/che/assembly                          # Generates binary assemblies of Che
/che/assembly/assembly-main            # Final packaging phase
/che/assembly/assembly-ide-war         # Creates the IDE.war from plug-ins & core
/che/assembly/assembly-machine-war     # Creates the agent WAR from plug-ins & core
/che/assembly/assembly-machine-server  # Creates the agent server that goes into ws
/che/core                              # Shared libraries for server, agents, and plugins
/che/dashboard                         # JavaScript app user management
/che/dockerfiles                       # Various images for building and running Che
/che/plugins                           # IDE & agent plug-ins
/che/wsmaster                          # Libraries used by the Che server
/che/wsagent                           # Libraries used by workspace agents
```

### Repositories
Some dependencies are managed in separate repositories as part of the `http://github.com/eclipse` organization. These dependencies are forks of other important projects.
```
/che-lib                                  # Forked dependencies that require mods
/che-lib/swagger                          # Embeded API configuration
/che-lib/terminal                         # Our embedded Web terminal
/che-lib/websocket                        # For comms between workspaces and browsers
/che-lib/pty                              
/che-lib/che-tomcat8-slf4j-logback        # For Che's runtime environment
/che-dependencies                         # Maven dependencies used by che
/che-dev                                  # Code style and license header
/che-parent                               # Maven plugins and profiles
```

### Other Repositories
These are external repositories that provide additional tools for Eclipse Che.
```
http://github.com/codenvy/Dockerfiles             # Defines recipes used by stacks
http://github.com/codenvy/che-installer           # Windows and JAR installers
http://github.com/codenvy/che-tutorials           # SDK examples and tutorials
http://git.eclipse.org/c/www.eclipse.org/che.git  # eclipse.org/che Web site
http://github.com/codenvy/cli                     # Experimental CLI
```
