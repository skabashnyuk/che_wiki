# Theia IDE + Che questions

### What Theia image to use inside Che?

It is **eclipse/che-theia**, which is located [here](https://hub.docker.com/r/eclipse/che-theia/).
The version of this image consists of two parts: 
`[THEIA_VERSION]-[CHE_VERSION]`
- first one - the version of Theia inside the image
- second one - the Che version itself (ex. `eclipse/che-theia:0.3.10-nightly`, `eclipse/che-theia:0.3.10-6.7.0`, [etc](https://hub.docker.com/r/eclipse/che-theia/tags/)) 
 

### How to update Theia version, used in the image?

You need to change the value of argument `THEIA_VERSION` in [Dockerfile](https://github.com/eclipse/che/blob/master/dockerfiles/theia/Dockerfile).

Beware of the CQ to be created for each Theia version upgrade.

Patches are per Theia version, so no need to remove them.

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
./build.sh --build-args:GITHUB_TOKEN=$GITHUB_TOKEN,THEIA_VERSION=0.3.13 --tag:0.3.13-nightly
```
or using docker:

```
docker build -t eclipse/che-theia:0.3.13-nightly --build-arg GITHUB_TOKEN={your token} --build-arg THEIA_VERSION=0.3.13 .
```
### How to create workspace with Theia IDE?

### How to add existing extension to Theia IDE?

### How to add my extension to Theia IDE?

### How to add existing plug-in to Theia IDE?

### How to debug a Theia extension running in Che ?

### How to deploy Che + Theia in Openshift and Minishift ?
