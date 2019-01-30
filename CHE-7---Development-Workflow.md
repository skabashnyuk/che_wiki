The best way to understand how a project works or to debug an issue is to get the source, built it, and run it. We document the best practices for developing improvements to the product. Eclipse Che has four major subsystems: the Che server, the IDE (based on Eclipse Theia), the plugins, and the user dashboard (a JavaScript app). The workflow for each can be slightly different.

### How to create and test a Che 7 plugin from an existing VS Code extension

Complete the following steps to run a Che 7 plugin based on [VS Code extension](https://marketplace.visualstudio.com/vscode)

It is possible to install VS Code extensions from the marketplace by invoking the "Deploy plugin by id" command from the command palette (<F1> opens the command palette). When prompted for input, type "vscode:extension/<extension id>", where <extension id> stands for the id in the VS Code marketplace. You can find the id on the extension page under "unique identifier" (see here: https://marketplace.visualstudio.com/items?itemName=redhat.java). This comes in handy to test that the extension works inside theia. We are currently testing the VS Code plugin API inside Theia for completeness and correctness, so expect some road bumps.

1. Prepare a docker image based on `wsskeleton/theia-endpoint-runtime`. This image is used as runtime to launch VS Code plugins in sidecars and should additionally contain all necessary tools/software/plugin dependencies, for instance java, Go etc. A `Dockerfile` and image can be hosted anywhere and there are no restrictions or naming rules. [Here is](https://github.com/eclipse/che-theia/tree/master/dockerfiles/remote-plugin-runner-java8) an example for java8 image. 

2. Build and push image to Docker Hub. @riuvshin needs to be contacted if it is necessary to publish image under Eclipse foundation DockerHub account. It can be any other public Docker registry though.

3.  Prepare `meta.yaml` for desired plugin. Take a look at an example for a node debug plugin:

```yaml
id: ms-vscode.node-debug2
version: 1.31.1
type: VS Code extension
name: Node Debug
title: Node.js debugging support
description: Node Debug is the debugger for Node.js versions >= 8.0 https://marketplace.visualstudio.com/items?itemName=ms-vscode.node-debug2
icon: https://www.eclipse.org/che/images/logo-eclipseche.svg
attributes:
  extension: "vscode:extension/ms-vscode.node-debug2"
  container-image: "abazko/ms-vscode.node-debug2" 
```

*  `extension` attribute consists of prefix `vscode:extension/` and VS Code extension ID that can be retrieved from plugin details page at  [marketplace](https://marketplace.visualstudio.com/)

* `container-image` attribute contains the image name from the step #1 - `registry/org/repo:tag`. In the example above, registry is omitted since this is DockerHub. And if no tag is specified, `latest` is used by default.

4. Push `meta.yaml` to https://github.com. The list of [available plugins](https://github.com/eclipse/che-plugin-registry/tree/master/plugins). It may not be GitHub. It's enough to host your yaml anywhere it's accessible for plugin broker (Apache server etc).

5. Create workspace and add plugin url to the workspace config. 

Important notes:
* plugin's url in the workspace config should be the url to the raw content:
* the version of the plugin in meta.yaml has to be the same as a name of parent folder which contains thats file

```json
"attributes": {
    "editor": "org.eclipse.che.editor.theia:1.0.0",
    "plugins": "che-machine-exec-plugin:0.0.1,https://raw.githubusercontent.com/eclipse/che-plugin-registry/master/plugins/org.eclipse.che.samples.container-fortune:0.0.1"
  }
```
Please, note that the URL to meta.yaml should be a direct URL to file contents, not the page that contains/serves it (raw GitHub link in the example above).
