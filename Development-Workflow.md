The best way to understand how a project works or to debug an issue is to get the source, built it, and run it locally. We document the best practices for developing improvements to the product. Eclipse Che has three major subsystems: the Che server, the agents running within a workspace, and the user dashboard (a JavaScript app). The workflow for each can be slightly different.

### Incremental Build
### Errors and Warnings
### Validate Your Changes
### Debugging
### Unit Testing
### Linting
### Branching
### Pull Requests
### Etiquette

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
docker build -t che-server dockerfiles/che-server/Dockerfile .

# Now configure the che-launcher Docker image to use the Che image
# TODO: Instruction on how to modify the Dockerfile with right che-server reference
docker build -t che-launcher dockerfiles/che/Dockerfile .

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
# See: https://maven.apache.org/plugins/maven-patch-plugin/faq.html#Why_doesnt_this_work_on_Windows
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

### Repositories
These repositories are for the core project hosted at `http://github.com/eclipse`.
```
/che
/che/assembly                                             # Generates binary assemblies of Che
/che/assembly/assembly-main                               # Final packaging phase
/che/assembly/assembly-ide-war                            # Creates the IDE.war from plug-ins & core
/che/assembly/assembly-machine-war                        # Creates the agent WAR from plug-ins & core
/che/assembly/assembly-machine-server                     # Creates the agent server that goes into ws
/che/core                                                 # Libraries shared among server, agents, and plugins
/che/dashboard                                            # AngularJS app for managing Che
/che/plugins                                              # IDE & agent plug-ins
/che/wsmaster                                             # Libraries used by the Che server
/che/wsagent                                              # Libraries used by agents installed into workspaces

/che-lib                                                  # Forked dependencies that require mods
/che-lib/swagger
/che-lib/terminal
/che-lib/websocket
/che-lib/pty
/che-lib/che-tomcat8-slf4j-logback

# /che and /che-lib depend upon /che-dependencies
/che-dependencies                                          # Maven dependencies used by che
/che-dev                                                   # Code style and license header

# /che-dependencies and /che-dev depend upon /che-parent
/che-parent                                                # Maven plugins and profiles
```

### Other Repositories
These are external repositories that provide additional tools for Eclipse Che.
```
http://github.com/codenvy/Dockerfiles                      # Defines the images referenced by stacks in Che
http://github.com/codenvy/che-installer                    # Creates the Windows and JAR installer packages
http://github.com/codenvy/che-tutorials                    # SDK examples and tutorials (needs updating)
http://github.com/che-samples                              # GitHub organization with sample repos used in Che
http://git.eclipse.org/c/www.eclipse.org/che.git           # The content for eclipse.org/che Web site
http://github.com/codenvy/cli                              # Experimental CLI for managing Che workspaces on the CLI
```