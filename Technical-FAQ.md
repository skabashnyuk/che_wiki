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

### How to debug a Theia extension running in Che ?

### How to deploy Che + Theia in Openshift and Minishift ?

# Che on Osio
### How to clean up PV content on Osio
In very rare case, you may ending up with orphan workspace folders on osio. Here are the commands to clean them up.
#### oc login
To log in with the `oc` command line,
- Connect to https://console.starter-us-east-2.openshift.com/
- Click on `top right ? button` > `Command Line Tools`
- Click on the `Copy to Clipboard` button for the line `oc login https://api.starter-us-east-2.openshift.com --token=<hidden>` to copy the command with your secret.
- Having a shell with `oc` command available, paste and execute the command.

#### After login with `oc`
```
oc project xxxx-che # usually xxx-che is username-che
oc run cleanup --image=registry.access.redhat.com/rhel7 -- tail -f /dev/null
oc volume dc/cleanup --add -t pvc --name=cleanup --claim-name=claim-che-workspace --mount-path=/workspaces
oc rsh cleanup-X-XXXXX # you can get the name of the pod with `oc get po`
# find and remove the orphans workpace folders if any in the folder `/workspaces`
oc delete all -l app=cleanup # once the folders removed, delete the image
```