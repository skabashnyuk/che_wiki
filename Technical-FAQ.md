# Theia IDE + Che questions
https://stackoverflow.com/questions/tagged/eclipse-che+theia

### What Theia image to use inside Che?
It is **eclipse/che-theia**, which is located [here](https://hub.docker.com/r/eclipse/che-theia/).
The version of this image consists of two parts: 
`[THEIA_VERSION]-[CHE_VERSION]`
- first one - the version of Theia inside the image
- second one - the Che version itself (ex. `eclipse/che-theia:0.3.10-nightly`, `eclipse/che-theia:0.3.10-6.7.0`, [etc](https://hub.docker.com/r/eclipse/che-theia/tags/)) 
 
### Where can I find more details about the Theia Plugin API ?
Complete documentation is located in this Theia documentation section: https://github.com/theia-ide/theia/blob/master/packages/plugin/API.md

### How to add more Theia Plugin API ?
WIP documentation is located here: https://github.com/theia-ide/theia/blob/plugin-api-documentation/packages/plugin-ext/doc/how-to-add-new-plugin-api.md

### I can not start a multi container terminal in Che Theia on Minishift
With the error on the browser console:
```
Uncaught (in promise) Error: pods is forbidden: User "system:serviceaccount:mini-che:default" cannot list pods in the namespace "mini-che": User "system:serviceaccount:mini-che:default" cannot list pods in project "mini-che"
```
To fix this, provide privilege to your user:
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
oc set volume dc/cleanup --add -t pvc --name=cleanup --claim-name=claim-che-workspace --mount-path=/workspaces # Mount your persistent volume to the local path /workspaces
oc get pods #Identify the name of the active Che pod
oc rsh cleanup-X-XXXXX # Use the name found above here - this will log you in to the container with your workspaces mounted in the `/workspaces` folder
# find and remove the orphans workpace folders if any in the `/workspaces` using normal Unix shell commands
oc delete all -l run=cleanup # once the folders removed, delete the image
```

