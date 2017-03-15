The best way to understand how a project works or to debug an issue is to get the source, built it, and run it locally. We document the best practices for developing improvements to the product. Eclipse Che has three major subsystems: the Che server, the agents running within a workspace, and the user dashboard (a JavaScript app). The workflow for each can be slightly different.

## Build and Run From Source
### Dependencies
* Docker 1.8+
* Maven 3.3.1+
* Oracle or OpenJDK Java 1.8

The M2_HOME and M2 variables should be set correctly. OpenJDK Java 1.8 on Debian/Ubuntu linux requires "openjdk-8-jdk-headless" package. 

To build the Che core, you will need the maven-patch-plugin. Windows [does not support this plugin](http://maven.apache.org/plugins/maven-patch-plugin/faq.html#Why_doesnt_this_work_on_Windows), and we give instructions on how to skip this plugin when building. You can also optionally modify your build to [download the patch tool](http://gnuwin32.sourceforge.net/packages/patch.htm) and then add the patch tool to your `PATH`.

To build the user dashboard submodule, you will need npm, bower, gulp, and python.
- Python `v2.7.x`(`v3.x.x`currently not supported)
- Node.js `v4.x.x` (`v5.x.x` / `v6.x.x` are currently not supported)
- npm
  - bower
  - gulp
  - typings

Learn more about how to [build the dashboard submodule here](https://github.com/eclipse/che/tree/master/dashboard).

To [build the exec agent submodule](https://github.com/eclipse/che/tree/master/exec-agent), you will also need Go 1.6+. The exec agent submodule is a way to execute commands and stream process output logs with a websocket terminal. We use it as a replacement for "docker exec" CLI, as this gives us more fine-grained control over interacting with Docker containers.

### Clone
If you do not haven't done already, please clone the Che repository
```sh
git clone https://github.com/eclipse/che.git
```
If you want to develop an extension for Che, we recommend to checkout the latest tagged and stable version after cloning, e.g.:
```sh
git checkout tags/4.6.0
```

### Build and Run
In its purest form, Che runs as a Tomcat server. You can build Che to create an assembly that has an embedded Tomcat server. 

```sh
cd assembly/assembly-main
mvn clean install

# A new assembly is placed in:
cd che/assembly/assembly-main/target/eclipse-che-<version>/eclipse-che-<version>
```

You can then run this with the CLI (complete reference can be found [here](https://www.eclipse.org/che/docs/setup/cli/index.html)):
```sh
docker run <DOCKER_OPTIONS> -v <path-to-repo>:/repo \
                            -v <local-path>:/data \
                            -v /var/run/docker.sock:/var/run/docker.sock \
                            eclipse/che start
```

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

# If you have forked the repository, you can define maven flags permanently by
# editing /.mvn/.jvm.config. Engineers with advanced multi-core machines usually
# set it to:
-Xms512m -Xmx4g -Djava.net.preferIPv4Stack=true -Dgwt.compiler.localWorkers=4

# We also have a maven "fast" profile that provides the same flags:
mvn clean install -Pfast
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
Note: On windows with Docker Toolbox there are issues with symlinks

### Build Che Using Docker
If you want to avoid setting up the dependencies to build Che and its submodules, we provide a Docker image that has the dependencies necessary to build Che. You can mount Che source code from your host to the container and then compile the code within the container. 
```sh
# For Mac + Linux - replace $PWD with the root path to build:
docker run -it --rm --name build-che 
           -v "$HOME/.m2:/home/user/.m2" 
           -v "$PWD":/home/user/che-build 
           -w /home/user/che-build 
           eclipse/che-dev 
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

### Developers on Windows
The dashboard and subversion plugins require OS-specific libraries to complete compilation. These modules will fail on Windows. You can use the `eclipse/che-dev` Docker image to compile the code which contains all of the dependencies. 

Alternatively, you can skip building submodules by using `-pl '!dashboard'` with the maven command line.

## Validate Your Changes
We have integrated findbugs into the maven build system to generate warnings during the build. If your code generates new warnings or errors from findbugs, you must eliminate those issues before submitting the pull request. You can skip these checks by passing `-Dfindbugs.skip=true` to the maven build.

We have integrated [Error Prone](https://github.com/google/error-prone) to check the state of code when you execute a maven build. Error prone verification is required to pass for all code submissions.

License checks for submitted files are done within a maven build. You can skip these license checks with `-Dskip-validate-sources` maven option.
 
## Debugging
Che is a multi-node system with processes running within the browser, the Che server and within the workspace. The debugging tactics for each are different.

### Debugging Che Server

The Che server runs on Tomcat. You can activate jpda suspend mode for debugging initialization by adding in the `che.env`:
```
CHE_DEBUG_SUSPEND=true
```

To change che debug port, in the `che.env`:
```
CHE_DEBUG_PORT=8000
```

Start Che in development mode which is activated by passing `--debug` to any command on the CLI.

### Debugging Workspace Agent
The workspace agent deployed by Che into your workspace is always using Tomcat, which starts with JPDA mode by default. You can identify the address and port of the debugger: 
```
Dashboard -> Workspaces -> Runtime tab -> Servers

# Find the server with the `wsagent.debug` reference
wsagent.debug 4403 http	http://172.17.0.1:40037
```

### Debugging Che IDE extensions
Che IDE extensions are authored with Google Web Toolkit (GWT) and then compiled into JavaScript. GWT has a concept called Super Dev Mode, which allows you to debug Java extensions within the browser, even though they are running as JavaScript.

#### GWT Super Dev Mode for Eclipse

[Download the GWT SDK 2.8.0 zip](http://www.gwtproject.org/versions.html) from Google's site. You will need to explode it and save in a directory on your compuer.

[Install Google Plugin for Eclipse](https://developers.google.com/eclipse/docs/getting_started) You will be asked to install software for Google App Engine and other Google utilities. You only need the Eclipse plugin package.

In Eclipse, go to `Window > Preferences > Google > Web Toolkit > SDKs > Add`. You will need to specify the directory where GWT is installed. 

##### Setup Run Configuration
In Eclipse, go to `Run > Run Configurations`, select `Java Application`, right click and select `New`.

In the `Main` tab, add the project `assembly-ide-war` with main class as `com.google.gwt.dev.codeserver.CodeServer`.

`Program arguments` : `-style PRETTY -noincremental -src target/generated-sources/gen`
`VM Options` : `-Xmx2048m`

In the `Classpath` tab, go to `User Entries > Add External Jars`. Add:

1. `gwt-codeserver.jar` (in the directory where you unzipped GWT zip),
2. `gwt-dev.jar`, (also in the same directory)

In the `Source` tab, remove any non-existent source folders. This is uncommon, but if you see something like `src/text/java` then these folders should be removed.

#### GWT Super Dev Mode for IntelliJ  
[Download the GWT SDK 2.8.0 zip](http://www.gwtproject.org/versions.html) from Google's site. You will need to explode it and save in a directory on your compuer.

JetBrains has a helpful page. There is [just a single step](https://www.jetbrains.com/help/idea/2016.2/enabling-gwt-support.html).

Setup Run Configuration. In `Run > Edit Configurations > GWT Configuration`, add a new configuration:
* `Use Super Dev Mode`
* `Dev Mode parameters`: `-noserver -noincremental -style PRETTY`
* `VM options:` `-Xmx2048m`

#### Launch Che with Super Dev Mode
Run Che normally. You can use the CLI, the Che launcher, or Eclipse. Within your browser create a workspace and then identify the workspace name.  Open the workspace with the workspace name or ID that you captured, so this would be `http://<che-url>/che/<ws-name>`.

Click the `Dev Mode On` bookmark on your booksmark bar. A message will appear asking you to recompile the application.  Select the `_app` and compile it.


## Profiling
The Che server and the primary workspace agent deployed within a workspace have JVM runtimes. We use JProfiler as the primary performance profiling utility for the JVMs that are running within each of these notes. Our servers are running within Docker containers for each of these nodes. JProfiler needs to be added, configured, and exposed within the Dockerfiles used to run Che or a workspace. JProfiler will need an additional port exposed and you will have to find the ephemeral port mapping of the container when it is running.

```
# Dockerfile configuration for a workspace stack recipe with JProfiler
FROM eclipse/ubuntu_jdk8

RUN wget -q http://download-aws.ej-technologies.com/jprofiler/jprofiler_linux_8_1_2.tar.gz -P /tmp/ &&\
  sudo tar -xzf /tmp/jprofiler_linux_8_1_2.tar.gz -C /usr/local &&\
  rm /tmp/jprofiler_linux_8_1_2.tar.gz

ENV CATALINA_OPTS=" $CATALINA_OPTS -Dcom.sun.management.jmxremote.ssl=false \
                   -Dcom.sun.management.jmxremote.authenticate=false \
                   -agentpath:/usr/local/jprofiler8/bin/linux-x64/libjprofilerti.so=8849"

EXPOSE 8849
```
You then start a workspace that uses this recipe. Once started, you can use the Che workspace REST APIs to find the ephemeral port for `8849` or you can run `docker inspect <ws-container-id` which will provide the same info. Use the ephemeral port when making a profiler connection.
## Logging
We use SLF4J for logging within the IDE and [Logback](http://logback.qos.ch/manual/configuration.html) within server-side extensions.

For client-side logging, import `org.eclipse.che.ide.util.loging.Log` and then [register log messages](https://github.com/eclipse/che/blob/master/plugins/plugin-machine/che-plugin-machine-ext-client/src/main/java/org/eclipse/che/ide/extension/machine/client/perspective/terminal/TerminalPresenter.java#L136-136). These messages are only logged on the client-side and can be viewed and filtered from the browser console.

For server-side logging, add [Logback as a maven dependency](https://github.com/eclipse/che/blob/master/core/commons/che-core-commons-schedule/pom.xml#L48-L55) and then make [logging calls to your code](https://github.com/eclipse/che/blob/master/core/commons/che-core-commons-schedule/src/test/java/org/eclipse/che/commons/schedule/executor/CronExpressionTest.java#L159). To change the level of log messages that are displayed, add a [Logback configuration file to the module](https://github.com/eclipse/che/blob/master/core/commons/che-core-commons-schedule/src/test/resources/logback-test.xml).

In an assembly, there is a `tomcat/conf/logback.xml` which specifies the system-wide configuration for logging output.

## Unit Testing
All functionality requires a unit test. Unit tests are executed as part of the build with `mvn clean install` for any module. When writing tests you can use JUnit or TestNG [with the Maven Surefire plugin](http://maven.apache.org/surefire/maven-surefire-plugin/examples/testng.html). If you want to run only unit tests on a module, execute `mvn clean test`.

## Linting
We do not apply linting rules.

## Code Style
We provide [code style formatters](https://github.com/eclipse/che-dev/tree/master/che-codestyle/src/main/resources) for other IDEs. If you develop Che within Che, we apply our own code style formatting automatically.

## Work Branches
All branches in the Che repository need to be named after the matching issue number in GitHub. Please try to avoid pretty-named branches. When your pull request is merged to master, the developer that created the branch is responsible for removing the branch. We perform a branch review after each milestone.

## Documentation
Docs are maintained in a [separate repository](http://github.com/eclipse/che-docs). Docs are authored in Markdown and then we use Jekyll to transform it into static HTML. Docs are then hosted within the product and also available at www.eclipse.org/che/docs. When issuing a pull request for Che, you will be asked to verify if any docs need to be added in a cross-referenced PR for the docs repo.

## Copyright
As an Eclipse project, we follow Copyright guidelines offered at [Eclipse's site](https://eclipse.org/legal/eplfaq.php). You can add your company's name in the EPL header to link the Copyright to multiple companies. We use https://github.com/mycila/license-maven-plugin/ to ensure that all necessary files have an appropriate license header.
Unfortunately it cannot currently handle multiple Copyright owners. See 
https://github.com/mycila/license-maven-plugin/issues/119. As a workaround, we allow license check to be disabled for specific files. Add this extra configuration to the Maven's `pom.xml` as part of your pull request.

```
<build>
  <plugins>
    <plugin>
      <groupId>com.mycila</groupId>
      <artifactId>license-maven-plugin</artifactId>
      <configuration>
        <excludes>
          <exclude>**/**/CronExpression*.java</exclude>
        </excludes>
      </configuration>
    </plugin>
  </plugins>
</build>
```

## Pull Requests
Before we can accept a pull request, you'll need to sign a [Contributor License Agreement (CLA)](https://github.com/eclipse/che/wiki/Contributor-License-Agreement). It is an automated, one-time process.

To enable us to quickly review and accept your pull requests, always create one pull request per issue and link the issue in the pull request. Never merge multiple requests in one unless they have the same root cause. Be sure to follow our coding guidelines and keep code changes as small as possible. Pull requests should contain tests whenever possible and documentation where appropriate.

We require that each PR has:
- A descriptive title.
- A link to the issue that initiated the PR.
- Changelog: one line summary in markdown for the release's Changelog. 
- Docs: a link to a matching PR in http://github.com/eclipse/che-docs.
- Release Notes: markdown summary (as little or as much!) included by marketing when release notes are sent to users.

Bug fix PRs may not require docs or release notes. All PRs must have either a `kind/enhancement`, `kind/docs`, or `kind/bugs` label.

PR approvals require at least one other committer and a maintainer to authorize.  Current maintainers include Vitalii Parfonov, Gennady Azarenkov, Sergii Kabashnyuk, Viktor Kuzynetsov, Roman Iuvshin, Florent Benoit, and Tyler Jewell. PRs that include docs and release notes updates must also include a PM reviewer. PM reviewers include Brad Micklea, Stevan LeMeur, James Drummond, Eugene Ivantsov, or Tyler Jewell.

If a PR is ready for review from developers or PMs a `status/code-review` label is set. Once all approvals have been granted the `status/code-review` label is removed and `status/pending-merge` is added - this indicates that code reviews are completed and maintainers are waiting for a merge window to appear. 

Once an issue is in `status/pending-merge` and the maintainer is aware of the timeframe for merge, they may assign a milestone marker. Milestones are predictable and any PR merged will be taken into the next milestone. Every merged PR must have an assigned milestone.

We really value pull requests and maintainers work to include open pull requests into every sprint. Unfortunately, we are not able to accept every pull request. There are several reasons we may not accepts a pull request:

- Performance: One of Che's core values is to deliver a localhost-equivalent distributed workspace server. This means that workspaces must perform well in both real and perceived performance.
- User experience: Since we want to deliver a minimalist IDE, the UX should feel small and simple to navigate. We want to avoid cluttering. Most changes to the UI need to be approved by the UX team.
- Architectural: The team and/or feature owner needs to agree with any architectural impact a change may make. Things like new extension APIs must be discussed with and agreed upon by the feature owner.
- Support: We receive >100 support requests each week, and it is a major commitment to supporting the needs of users ongoing. If a change to the product could introduce unknown complications around supportability, then we will be cautious until there is an abundance of documentation and awareness on the implications.

To improve the chances to get a pull request merged you should select an issue that is labeled with a `level/*` label or `kind/bug` label. If the issue you want to work is not labeled with either of these, you can start a conversation with the issue owner asking how you can help.

## Etiquette
In order to keep the conversation clear and transparent, please limit discussion to English and keep things on topic with the issue. Be considerate to others and try to be courteous and professional at all times. Everyone participating in the project must follow the [Eclipse Community Code of Conduct](https://www.eclipse.org/org/documents/Community_Code_of_Conduct.php).

## Repository Layout
### Modules
Our repository is broken in a variety of independently buildable submodules.
```
/che
/che/agents                            # Software deployed into workspaces
/che/agents/exec                       # Embedded web terminal
/che/agents/ls-csharp                  # C# intellisense
/che/agents/ls-json                    # JSON intellisense
/che/agents/ls-python                  # Python intellisense
/che/agents/ls-php                     # PHP intellisense
/che/agents/ls-typescript              # TypeScript intellisense
/che/agents/unison                     # Unison file synchronizer
/che/agents/ssh                        # SSH server
/che/assembly                          # Generates binary assemblies of Che
/che/assembly/assembly-main            # Final packaging phase
/che/assembly/assembly-ide-war         # Creates the IDE.war from plug-ins & core
/che/assembly/assembly-machine-war     # Creates the agent WAR from plug-ins & core
/che/assembly/assembly-machine-server  # Creates the agent server that goes into ws
/che/core                              # Shared libraries for server, agents, and plugins
/che/dashboard                         # JavaScript app user management
/che/dockerfiles                       # Docker images to run Che, CLI, & utilities
/che/ide                               # The browser-based IDE
/che/plugins                           # IDE & workspace agent plug-ins
/che/samples                           # Code templates injected into new workspaces
```

### Repositories
Some dependencies are managed in separate repositories as part of the `http://github.com/eclipse` organization. These dependencies are forks of other important projects, contain shared libraries that need to be managed on a different tagging lifecycle than Che, or have very large files within them (such as docs).
```
https://github.com/eclipse/che-archetypes
https://github.com/eclipse/che-dependencies
https://github.com/eclipse/che-dev
https://github.com/eclipse/che-dockerfiles
https://github.com/eclipse/che-docs
https://github.com/eclipse/che-lib
https://github.com/eclipse/che-parent
```

### Other Repositories
These are external repositories that provide additional tools for Eclipse Che.
```
http://github.com/codenvy/che-installer           # Windows and JAR installers
http://github.com/codenvy/che-tutorials           # SDK examples and tutorials
http://git.eclipse.org/c/www.eclipse.org/che.git  # eclipse.org/che Web site
```
