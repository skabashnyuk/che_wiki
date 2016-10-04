The best way to understand how a project works or to debug an issue is to get the source, built it, and run it locally. We document the best practices for developing improvements to the product. Eclipse Che has three major subsystems: the Che server, the agents running within a workspace, and the user dashboard (a JavaScript app). The workflow for each can be slightly different.

## Build and Run From Source
### Dependencies
* Docker 1.8+
* Maven 3.3.1+
* Oracle Java 1.8 -- compilation with openjdk is not yet supported

The M2_HOME and M2 variables should be set correctly.

To build the Che core, you will need the maven-patch-plugin. Windows [does not support this plugin](http://maven.apache.org/plugins/maven-patch-plugin/faq.html#Why_doesnt_this_work_on_Windows), and we give instructions on how to skip this plugin when building. You can also optionally modify your build to [download the patch tool](http://gnuwin32.sourceforge.net/packages/patch.htm) and then add the patch tool to your `PATH`.

To build the user dashboard submodule, you will need npm, bower, gulp, and python. 

### Clone
If you do not haven't done already, please clone the Che repository
```sh
git clone https://github.com/eclipse/che.git
```
If you want to develop an extension for Che, we recommend to checkout the latest tagged and stable version after cloning, e.g.:
```sh
git checkout tags/4.6.0
```

### Build and Run - Tomcat
In its purest form, Che runs as a Tomcat server. You can build Che to create an assembly that has an embedded Tomcat server. You can run this without launching Docker.

```sh
cd che/assembly
mvn clean install

# A new assembly is placed in:
cd che/assembly/assembly-main/target/eclipse-che-<version>/eclipse-che-<version>

# Executable files are:
bin/che.sh
bin/che.bat
```
Che will be available at ```localhost:8080```. You can also optionally use the Che Docker launcher as your client and set the `CHE_LOCAL_BINARY` to point to the location of your assembly. The Docker container will volume mount the compiled binary from your system for its run.

```sh
# You can build Che and all submodules in the root directory.
cd che/
mvn clean install

# Each submodule may require additional software to build properly.
# You can skip a submodule to avoid installing additional software.
# For example, to skip building the dashboard:
mvn -pl '!dashboard' clean install

# There is additional software that you need to run unit tests and license checks.
# Build faster by skipping unit tests and other enforcement features:
mvn -DskipTests=true \
    -Dfindbugs.skip=true \
    -Dskip-validate-sources \
    -Dmdep.analyze.skip=true \
    -Dlicense.skip=true \
    -Dgwt.compiler.localWorkers=2 -T 1C \
     clean install
```

### Build and Run - Docker
We distribute Eclipse Che as a Docker image and this is the preferred way for users to install and run Che. You can use our Che launcher [to run your local Che binaries](https://eclipse-che.readme.io/docs/usage-docker#local-eclipse-che-binaries), or you can create a new Docker image that contains your binaries.

```sh
# If your local assembly is located at /home/assembly:
docker run -v /var/run/docker.sock:/var/run/docker.sock \
           -e CHE_LOCAL_BINARY=/home/assembly \           
           codenvy/che-launcher:nightly start

# Build the Che server Docker image from the root of our source:
docker build -t che-server -f dockerfiles/che-server/Dockerfile .
docker tag <imageid> codenvy/che-server:<choose-a-version>

# Now configure the che-launcher Docker image to use the Che image
docker build -t che-launcher -f dockerfiles/che/Dockerfile .
docker tag <imageid> codenvy/che-launcher:<match-version-of-server>

# Now run Che
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock \
       codenvy/che-launcher:<version> start 
```
Community member Ilya Buzuik has published [an article](https://github.com/ibuziuk/docs/blob/master/che_remote_debugging.adoc) on how to setup remote debugging of a Che assembly.

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
Note: On windows with Docker Toolbox there are issues with symlinks

### Build Che Using Docker
If you want to avoid setting up the dependencies to build Che and its submodules, we provide a Docker image that has the dependencies necessary to build Che. You can mount Che source code from your host to the container and then compile the code within the container. 
```sh
# For Mac + Linux - replace $PWD with the root path to build:
docker run -it --rm --name build-che 
           -v "$HOME/.m2:/home/user/.m2" 
           -v "$PWD":/home/user/che-build 
           -w /home/user/che-build 
           codenvy/che-dev 
           mvn -DskipTests=true 
               -Dfindbugs.skip=true
               -Dgwt.compiler.localWorkers=2 -T 1C 
               -Dskip-validate-sources 
               -Dmdep.analyze.skip=true 
               -Dlicense.skip=true
               clean install
               
# For Windows, replace $HOME with maven repo directory.
# For Windows, replace $PWD with Che source code directory.
```

## Validate Your Changes
We have integrated findbugs into the maven build system to generate warnings during the build. If your code generates new warnings or errors from findbugs, you must eliminate those issues before submitting the pull request. You can skip these checks by passing `-Dfindbugs.skip=true` to the maven build.

We have integrated [Error Prone](https://github.com/google/error-prone) to check the state of code when you execute a maven build. Error prone verification is required to pass for all code submissions.

License checks for submitted files are done within a maven build. You can skip these license checks with `-Dskip-validate-sources` maven option.
 
## Debugging
Che is a multi-node system with processes running within the browser, the Che server and within the workspace. The debugging tactics for each node is different. These tactics are covered in the [plugin development resource center](https://eclipse-che.readme.io/docs/setup-che-workspace).  

## Logging
We use SLF4J for logging within the IDE and [Logback](http://logback.qos.ch/manual/configuration.html) within server-side extensions.

For client-side logging, import `org.eclipse.che.ide.util.loging.Log` and then [register log messages](https://github.com/eclipse/che/blob/master/plugins/plugin-machine/che-plugin-machine-ext-client/src/main/java/org/eclipse/che/ide/extension/machine/client/perspective/terminal/TerminalPresenter.java#L136-136). These messages are only logged on the client-side and can be viewed and filtered from the browser console.

For server-side logging, add [Logback as a maven dependency](https://github.com/eclipse/che/blob/master/core/commons/che-core-commons-schedule/pom.xml#L48-L55) and then make [logging calls to your code](https://github.com/eclipse/che/blob/master/core/commons/che-core-commons-schedule/src/test/java/org/eclipse/che/commons/schedule/executor/CronExpressionTest.java#L159). To change the level of log messages that are displayed, add a [Logback configuration file to the module](https://github.com/eclipse/che/blob/master/core/commons/che-core-commons-schedule/src/test/resources/logback-test.xml).

In an assembly, there is a `tomcat/conf/logback.xml` which specifies the system-wide configuration for logging output.

## Unit Testing
All functionality requires a unit test. Unit tests are executed as part of the build with `mvn clean install` for any module. When writing tests you can use JUnit or TestNG [with the Maven Surefire plugin](http://maven.apache.org/surefire/maven-surefire-plugin/examples/testng.html). If you want to run only unit tests on a module, execute `mvn clean test`.

## Linting
We do not apply linting rules.

## Work Branches
All branches in the Che repository need to be named after the matching issue number in GitHub. Please try to avoid pretty-named branches. When your pull request is merged to master, the developer that created the branch is responsible for removing the branch. We perform a branch review after each milestone.

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
/che/plugins                           # IDE & agent plug-ins
/che/wsmaster                          # Libraries used by the Che server
/che/wsagent                           # Libraries used by workspace agents
```

### Repositories
Some dependencies are managed in separate repositories as part of the `http://github.com/eclipse` organization. These dependencies are forks of other important projects.
```
/che-dockerfiles                          # Dockerfiles for our stacks (dozens!) and utilities like launcher
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
http://github.com/codenvy/che-installer           # Windows and JAR installers
http://github.com/codenvy/che-tutorials           # SDK examples and tutorials
http://git.eclipse.org/c/www.eclipse.org/che.git  # eclipse.org/che Web site
```
