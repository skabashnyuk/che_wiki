The best way to understand how a project works or to debug an issue is to get the source, built it, and run it locally. We document the best practices for developing improvements to the product. Eclipse Che has three major subsystems: the Che server, the agents running within a workspace, and the user dashboard (a JavaScript app). The workflow for each can be slightly different.

## Build and Run From Source
### Dependencies
* Docker 1.8+
* Maven 3.3.1+
* Oracle or OpenJDK Java 1.8
* Go 1.6.3

The M2_HOME and M2 variables should be set correctly. OpenJDK Java 1.8 on Debian/Ubuntu linux requires `openjdk-8-jdk-headless` package. 

To build the Che core, you will need the maven-patch-plugin. Windows [does not support this plugin](http://maven.apache.org/plugins/maven-patch-plugin/faq.html#Why_doesnt_this_work_on_Windows), and we give instructions on how to skip this plugin when building. You can also optionally modify your build to [download the patch tool](http://gnuwin32.sourceforge.net/packages/patch.htm) and then add the patch tool to your `PATH`.

To build the user dashboard submodule, you will need npm, bower, gulp, and python.
- Python `v2.7.x`(`v3.x.x`currently not supported)
- Node.js `v4.x.x` (`v5.x.x` / `v6.x.x` are currently not supported)
- npm
  - bower
  - gulp
  - typings

Learn more about how to [build the dashboard submodule here](https://github.com/eclipse/che/tree/master/dashboard).

To [build the exec agent submodule](https://github.com/eclipse/che/tree/master/agents/exec), you will also need Go 1.6+. The exec agent submodule is a way to execute commands and stream process output logs with a websocket terminal. We use it as a replacement for "docker exec" CLI, as this gives us more fine-grained control over interacting with Docker containers.

### Clone
If you haven't done so already, please clone the Che repository
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

You can then run this with the CLI (complete reference can be found [here](https://www.eclipse.org/che/docs/docker-cli.html)):
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
    -Dmdep.analyze.skip=true \
    -Dlicense.skip=true \
    -Dgwt.compiler.localWorkers=2 -T 1C \
    -Pnative \
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
mvn -DskipTests=true -Dfindbugs.skip=true clean install
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
               -Dmdep.analyze.skip=true 
               -Dlicense.skip=true
               -Pnative
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

License checks for submitted files are done within a maven build. You can skip these license checks with `-Dlicense.skip` maven option.
 
## IDE Setup
You can build (and run) Che from within another IDE. Our engineers use Eclipse and IntelliJ for development.

### Eclipse IDE - Yatta Installer
Yatta is great and they [maintain an Oomph installer](https://profiles.yatta.de/iQBd) for Eclipse Che. It will install Eclipse, some additional Eclipse plugins, and checkout the Che source code. If you are using OpenJDK on your system, you will need to install OpenJFX first.

We recommend that you deactivate automatic builds in Eclipse to disable running maven in places you do not want it to. 

### Eclipse IDE - Classic Installer
You can use the standard Eclipse installer. Make sure you are using the [Eclipse IDE for Java](https://www.eclipse.org/downloads/eclipse-packages/) configured with the maven plugin.

Separately, you will need to have Eclipse Che source code cloned on your file system. Use `Import > Maven > Existing Maven Projects` to import Che and select all projects to be imported. 

You will need to define a maven command to bud Che. Create a "Run Configuration" and in the Maven Build section choose `assembly-main` to be the base directory. Add a new goal named `clean install` and select `Skip Tests` checkbox. This will create a command that will build Che.

You may have to setup additional environment variables for a custom command.  If you run into any `npm` errors, this is due to permission and you need to remove your NPM repository `.npm` folder.

If you get a clean compilation, the assembly will be built into the `assembly/assembly-main` folder and you can use our Docker CLI syntax to run the assembly. This syntax can be setup as a run configuration within Eclipse.

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

You also need to add the following to `che.env`, otherwise it will default to `PRODUCTION` and ignore the debug settings:
```
CHE_ENVIRONMENT="development"
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

In the `Arguments` tab: 

`Program arguments` : `-style PRETTY -noincremental -src target/generated-sources/gen org.eclipse.che.ide.IDE`  
`VM Arguments` : `-Xmx2048m`

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

By default, Eclipse Che uses [Google Java style formatting](https://github.com/google/google-java-format). There are several ways to apply this formatting (listed in priority order):

* maven plugin is enabled by default in a build cycle (it does not format but checks compliance with code style). If the build fails with an error indicating non-complying files, run `mvn fmt:format` to fix errors.
* there are [IntelliJ](https://plugins.jetbrains.com/plugin/8527-google-java-format) and [Eclipse](https://github.com/google/google-java-format/releases/download/google-java-format-1.3/google-java-format-eclipse-plugin-1.3.0.jar) plugins that will auto-format Java source files. Sometimes, these IDE plugins may produce slightly different formatting results as compared to the Maven plugin. If compilation fails due to a compliance check, run `mvn fmt:format` to fix errors.
* Google Java Formatter isn't implemented for Eclipse Che itself. You're welcome to follow [this issue](https://github.com/eclipse/che/issues/339) though.

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

We always require that each PR has:
- A descriptive title.
- A link to the issue that initiated the PR if one exists.
- Changelog: one line summary in markdown for the release's Changelog. 

We may require that each PR has:
- Docs: a link to a matching PR in http://github.com/eclipse/che-docs.
- Release Notes: markdown summary (as little or as much!) included by marketing when release notes are sent to users.

Bug fix PRs may not require docs or release notes. All PRs must have either a `kind/enhancement`, `kind/docs`, or `kind/bugs` label.

PR approvals require at least one other committer and a maintainer to authorize.  Current maintainers include Vitalii Parfonov, Gennady Azarenkov, Sergii Kabashnyuk, Viktor Kuzynetsov, Roman Iuvshin, Florent Benoit, Mario Loriedo and Tyler Jewell. PRs that include docs and release notes updates must also include a PM reviewer. PM reviewers include Brad Micklea, Stevan LeMeur, Eugene Ivantsov, or Tyler Jewell.

If a dispute arises between multiple parties on a pull request on the best forward direction, we encourage the parties to work through any differences of opinion within the thread. If a deadlock occurs, then the maintainer assigned to the PR will have decision authority.

To have approval from [Che QE team](https://github.com/orgs/eclipse/teams/eclipse-che-qa), PR should comply with conditions described in [Checklist](https://github.com/eclipse/che/wiki/Checklist-of-pull-request-approval-by-Eclipse-Che-QE-team).

If a PR is ready for review from developers or PMs a `status/code-review` label is set. Once all approvals have been granted the `status/code-review` label is removed and `status/pending-merge` is added - this indicates that code reviews are completed and maintainers are waiting for a merge window to appear. 

Once an issue is in `status/pending-merge` and the maintainer is aware of the time frame for merge, they may assign a milestone marker. Milestones are predictable and any PR merged will be taken into the next milestone. Every merged PR must have an assigned milestone.

We really value pull requests and maintainers work to include open pull requests into every sprint. Unfortunately, we are not able to accept every pull request. There are several reasons we may not accepts a pull request:

- Performance: One of Che's core values is to deliver a localhost-equivalent distributed workspace server. This means that workspaces must perform well in both real and perceived performance.
- User experience: Since we want to deliver a minimalist IDE, the UX should feel small and simple to navigate. We want to avoid cluttering. Most changes to the UI need to be approved by the UX team.
- Architectural: The team and/or feature owner needs to agree with any architectural impact a change may make. Things like new extension APIs must be discussed with and agreed upon by the feature owner.
- Support: We receive >100 support requests each week, and it is a major commitment to supporting the needs of users ongoing. If a change to the product could introduce unknown complications around supportability, then we will be cautious until there is an abundance of documentation and awareness on the implications.

To improve the chances to get a pull request merged you should select an issue that is labeled with a `level/*` label or `kind/bug` label. If the issue you want to work is not labeled with either of these, you can start a conversation with the issue owner asking how you can help.

## Long-Lived Branches
We generally prefer that committers work on features using long-lived branches within our repositories instead of making a fork into another repository. This allows for the main repository to maintain a history of activity against the project and also provides a higher degree of transparency for the community at large.

Branch owners can define their own policies for how changes are merged, whether directly with a push or with a branch PR. Branch PRs against long-lived branches are a good practice when teams include multiple engineers or there needs to be a discussion on the structure of the change request. Branch PRs should have the `target/branch` label added. Branch PRs do not have to meet the same quality standard prior to being merged including documentation, changelog, release notes, and code formatting. However, eventually long-lived branches are usually targeted for master, so the higher standard applied to intermediate PRs will likely make the master PR process smoother.

## Etiquette
In order to keep the conversation clear and transparent, please limit discussion to English and keep things on topic with the issue. Be considerate, courteous, and professional. Everyone participating in the project must follow the [Eclipse Community Code of Conduct](https://www.eclipse.org/org/documents/Community_Code_of_Conduct.php).

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

How to run Selenium tests
------------------

#### 1. Register OAuth application 

Go to [OAuth application page](https://github.com/settings/applications/new) and register a new application:
* `Application name` : `Che`
* `Homepage URL` : `http://<YOUR_IP_ADDRESS>:8080`
* `Application description` : `Che`
* `Authorization callback URL` : `http://<YOUR_IP_ADDRESS>:8080/api/oauth/callback`

Substitute `CHE_OAUTH_GITHUB_CLIENTID` and `CHE_OAUTH_GITHUB_CLIENTSECRET` properties in `che.env` with `Client ID` and `Client Secret` taken from 
newly created [OAuth application](https://github.com/settings/developers).

#### 2. Add configuration file

Set `CHE_LOCAL_CONF_DIR` environment variable and point to the folder where selenium tests configuration will be stored.
Create file `selenium.properties` in that folder with the following content:
```
# GitHub account credentials
github.username=<MAIN_GITHUB_USERNAME>
github.password=<MAIN_GITHUB_PASSWORD>
github.auxiliary.username=<AUXILIARY_GITHUB_USERNAME>
github.auxiliary.password=<AUXILIARY_GITHUB_PASSWORD>

# Google account credentials (IMAP has to be enabled)
google.user=<GOOGLE_USER>
google.password=<GOOGLE_PASSWORD>
```

#### 3. Prepare repository 
Fork all repositories from [https://github.com/idexmai?tab=repositories](https://github.com/idexmai?tab=repositories) into the main GitHub account.
Fork the repository [https://github.com/iedexmain1/pull-request-plugin-fork-test](https://github.com/iedexmain1/pull-request-plugin-fork-test) into the auxiliary GitHub account.

#### 4. Start Eclipse Che

Follow the guide: [https://github.com/eclipse/che](https://github.com/eclipse/che)

#### 5. Run tests

Simply launch `./selenium-tests.sh`

Run tests configuration properties
--------------------------------------
```
Usage: ./selenium-tests.sh [-Mmode] [options] [tests scope]

Options:
    --http                              Use 'http' protocol to connect to product
    --https                             Use 'https' protocol to connect to product
    --host=<PRODUCT_HOST>               Set host where product is deployed

Modes (defines environment to run tests):
    local                               All tests will be run in a Web browser on the developer machine.
                                        Recommended if test visualization is needed and for debugging purpose.

        Options that go with 'local' mode:
        --web-driver-version=<VERSION>  To use the specific version of the WebDriver, be default the latest will be used: 2.30
        --web-driver-port=<PORT>        To run WebDriver on the specific port, by default: 9515
        --threads=<THREADS>             Number of tests that will be run simultaneously. It also means the very same number of
                                        Web browsers will be opened on the developer machine.
                                        Default value is in range [2,5] and depends on available RAM.


    grid (default)                      All tests will be run in parallel among several docker containers.
                                        One container per thread. Recommended to run test suite.

        Options that go with 'grid' mode:
            --threads=<THREADS>         Number of tests that will be run simultaneously.
                                        Default value is in range [2,5] and depends on available RAM.

Define tests scope:
    --all-tests                         Run all tests within the suite despite of <exclude>/<include> sections in the test suite.
    --test=<TEST_CLASS>                 Single test to run
    --suite=<SUITE>                     Test suite to run, found:
                                            * CheSuite.xml

Handle failing tests:
    --failed-tests                      Rerun failed tests that left after the previous try
    --regression-tests                  Rerun regression tests that left after the previous try
    --rerun                             Automatically rerun failing tests
    --compare-with-ci                   Compare failed tests with results on CI server

Other options:
    --debug                             Run tests in debug mode

HOW TO of usage:
    Test Eclipse Che assembly:
        ./selenium-tests.sh -Mgrid

    Test Eclipse Che assembly and automatically rerun failing tests:
        ./selenium-tests.sh -Mgrid --rerun

    Run single test or package of tests:
        ./selenium-tests.sh <...> --test=<TEST>

    Run suite:
        ./selenium-tests.sh <...> --suite=<PATH_TO_SUITE>

    Rerun failed tests:
        ./selenium-tests.sh <...> --failed-tests
        ./selenium-tests.sh <...> --failed-tests --rerun

    Debug selenium test:
        ./selenium-tests.sh -Mlocal --test=<TEST> --debug

    Analyse tests results:
        ./selenium-tests.sh --compare-with-ci [CI job number]
```

