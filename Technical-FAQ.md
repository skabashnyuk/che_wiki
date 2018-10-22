# Theia IDE + Che questions

### What Theia image to use inside Che?

It is **eclipse/che-theia**, which is located [here](https://hub.docker.com/r/eclipse/che-theia/).
The version of this image consists of two parts: 
`[THEIA_VERSION]-[CHE_VERSION]`
- first one - the version of Theia inside the image
- second one - the Che version itself (ex. `eclipse/che-theia:0.3.10-nightly`, `eclipse/che-theia:0.3.10-6.7.0`, [etc](https://hub.docker.com/r/eclipse/che-theia/tags/)) 
 

### How to update Theia version, used in the image?

You need to change the value of argument `THEIA_VERSION` in [Dockerfile](https://github.com/eclipse/che/blob/master/dockerfiles/theia/Dockerfile).

Beware of the CQ to be created for each Theia version upgrade.<br/>
Patches are per Theia version, so no need to remove them.<br/>
Integration tests are executed by default. Upgrading Theia may require updating integration tests.

### How to update Theia image with patches to avoid upgrading Theia version ?
Patches are per version
let say you want to patch 0.3.12 version
you put patches in `dockerfiles/theia/src/patches/0.3.12` folder and name your patches like `001-this-is-my.patch` , `002-another.patch`

For `0.3.13`, patches will go in `dockerfiles/theia/src/patches/0.3.13`, etc

### How to build Che Theia image with my own changes?

The sources of eclipse/che-theia is located [here](https://github.com/eclipse/che/tree/master/dockerfiles/theia).
After the changes are made, you need to rebuild the image with the following command:
using build script:
```
$ ./build.sh --build-args:GITHUB_TOKEN=$GITHUB_TOKEN,THEIA_VERSION=0.3.13 --tag:0.3.13-nightly
```
or using docker:

```
$ docker build -t eclipse/che-theia:0.3.13-nightly --build-arg GITHUB_TOKEN={your token} --build-arg THEIA_VERSION=0.3.13 .
```

Integration tests are launched by default during the build. It is possible to skip with the option `--skip-tests`

```
./build.sh --skip-tests
```

### How to create workspace with Theia IDE?

### How to add existing extension to Theia IDE?

### How to add my extension to Theia IDE?

### How to create a new plug-in to Theia or Che-theia IDE ?
You can use the yeoman generator as describe here: https://www.theia-ide.org/doc/Authoring_Plugins.html

### How to add existing plug-in to Theia IDE?

### Where can I find more details about the Theia Plugin API ?
Complete documentation is located in this Theia documentation section: https://github.com/theia-ide/theia/blob/master/packages/plugin/API.md

### How to add more Theia Plugin API ?
WIP documentation is located here: https://github.com/theia-ide/theia/blob/plugin-api-documentation/packages/plugin-ext/doc/how-to-add-new-plugin-api.md

### How to debug a Theia extension running in Che ?

### How to debug a Theia plugin running in Che ?

#### Frontend plugin

To debug frontend plugin switch to hosted instance tab in browser and open Developer Tools by pressing `F12` or `Ctrl+Shift+I`. After this you should see something like this (all screenshots here is for Google Chrome, but the flow is similar for other browsers):
![chrome-open-dev-console](https://user-images.githubusercontent.com/15607393/46793343-26638680-cd4e-11e8-9a8e-5af1b7613b1f.png)

Now switch to Sources tab and press `Ctrl+P` to open source files search. Then start typing name of file you want to debug and select it from the drop down list:
![chrome-dev-console-source-search](https://user-images.githubusercontent.com/15607393/46793414-57dc5200-cd4e-11e8-8235-86f3e6d68725.png)

Note, you should select original file (for example with ts extension for plugin written in typescript) to be able to see non minimized sources.
When file is opened, find code you want to debug and set breakpoint(s). To do this just click on line number and blue marker should appear. This means that breakpoint is set. Also list of all breakpoint is displayed in Breakpoints section in the right panel.
![chrome-dev-console-breakpoint-and-theia-command](https://user-images.githubusercontent.com/15607393/46793430-60cd2380-cd4e-11e8-9fa1-d52056dd16d8.png)

When breakpoints are set we need to get line with breakpoint executed. To reach it, invoke corresponding command or trigger needed event from IDE. Then line with breakpoint should be highlighted and debug information appear in the right panel.
![chrome-dev-console-debugger-paused-on-breakpoint](https://user-images.githubusercontent.com/15607393/46793438-64f94100-cd4e-11e8-9830-7fab0f2b0eaa.png)

At this point it is possible to examine current state of the code, make some changes in values, etc.
When debugger is paused on breakpoint
 - To know which value some variable holds at this moment see Scope section of right panel. If searched variable is declared as local in current block it may be found in Local section. Another way is to just hover mouse pointer over needed variable and popup with its value will appear.
 - To monitor result of some expression use Watch section in the right panel. Just add needed value and it will recalculate it on each step. 
 - To change variable value find it the right panel (Scope section) and double click on its value then edit will appear.
 - To know which function called current one open Call Stack section. If select a frame all the data will be updated and it is possible to examine state of plugin in that scope.
 - To execute any javascript code press `Esc` and type commands.

To control execution use toolbar in the right upper corner or hotkeys:
 - Resume script execution (`F8`) - continue execution of script
 - Step over next function call (`F10`) - executes next function in current line as a step
 - Step into next function call (`F11`) - enters into next function and stops on its first instruction
 - Step (`F9`) - similar to Step into, but doesn’t enter asynchronous functions.
 - Deactivate breakpoints (`Ctrl+F8`) - disables all breakpoints and allows to release execution fast.
 - Pause on exceptions button - forces to stops execution on any exception occurrence.

Important note. Sometimes it is impossible to set a breakpoint in some places or some local variables is not visible in local scope. This is the result of script optimization, so if a local variable declared and used only in one place it might became just inline value in result script.

If one need to debug code which executes on page load just set breakpoints in needed places and reload page (use reload button or just hit `F5`). 

For more details how to use Developer Tools see:
 - [Google Chrome](https://developers.google.com/web/tools/chrome-devtools/)
 - [Firefox](https://developer.mozilla.org/en-US/docs/Tools)

When some changes are made to plugin one should recompile the plugin and then just reload page of hosted instance.

#### Backend plugin

### How to deploy Che + Theia in Openshift and Minishift ?

### I can not start a multi container terminal in Che Theia on Minishift
With the error on the browser console:
```
Uncaught (in promise) Error: pods is forbidden: User "system:serviceaccount:mini-che:default" cannot list pods in the namespace "mini-che": User "system:serviceaccount:mini-che:default" cannot list pods in project "mini-che"
```
To fix this, you can provide privilege to your user:
```
oc login -u system:admin
oc adm policy add-cluster-role-to-user admin system:serviceaccount:mini-che:default
```

# Che on OpenShift.io

### How do I figure out where my workspace is running?
To figure out which cluster your workspace is running in:

1. Connect to the openshift.io dashboard
2. Create a new space ("New space" in top left corner)
3. Create a test project by clicking the "Create an application" button, and following the wizard
4. Kick off a pipeline and view its progress. You should see the application in Stage section of the applciation view.
5. Click on the "Build #x" link for the pipeline, you will be taken to an OpenShift Online cluster
6. In the OpenShift Online console, there are multiple namespaces with a common root available in a drop-down at the top left, including -che, -jenkins, -run, and -stage. Select the "username-che" namespace

You are now looking at the OpenShift project which contains your Che workspaces.

### How to clean up PV content on Osio
Performance when starting workspaces is affected by the number of files in your Persistent Volume in the Che namespace on OpenShift. When projects are deleted, you may ending up with several workspace folders with lots of files on this volume.

You can connect directly to OpenShift, attach this volume to another container, and remove any files which you do not require any more. Here are the commands to clean them up.

#### Connecting to OpenShift from the command line

To connect to OpenShift, you first need to install the `oc`command line tool, and log in to your OpenShift instance.

To log in with the `oc` command line,
- [Install the OpenShift CLI tools](https://docs.openshift.com/container-platform/3.11/cli_reference/get_started_cli.html)
- Find the OpenShift instance your account is allocated to (by following the previous question)
- Connect to the OpenShift dashboard you found (eg. https://console.starter-us-east-2.openshift.com/)
- Click on your username in the top right, and in the pop-up menu, `Copy Login command`
- Paste and execute the line into a local terminal - it should be in the form `oc login https://api.starter-us-east-2.openshift.com --token=<hidden>`

#### Cleaning up storage space
After logging in to OpenShift (see previous question), you can attach to a container with this volume mounted, and clean up the files:
```
oc project xxxx-che # usually xxx-che is username-che - selects your Che project
oc run cleanup --image=registry.access.redhat.com/rhel7 -- tail -f /dev/null # This file will remove unused images from your local instance cache
oc volume dc/cleanup --add -t pvc --name=cleanup --claim-name=claim-che-workspace --mount-path=/workspaces # Mount your persistent volume to the local path /workspaces
oc get pods #Identify the name of the active Che pod
oc rsh cleanup-X-XXXXX # Use the name found above here - this will log you in to the container with your workspaces mounted in the `/workspaces` folder
# find and remove the orphans workpace folders if any in the `/workspaces` using normal Unix shell commands
oc delete all -l app=cleanup # once the folders removed, delete the image
```

### How can I use Theia on che.openshift.io?

