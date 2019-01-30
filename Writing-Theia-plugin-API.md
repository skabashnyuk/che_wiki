
Theia can be extended at runtime by writing plugins. Plugins are javascript programs that are run either in a node instance (back-end plugins) or in a web worker (front-end plugins)

# Relevant theia packages:
* /plugin
Contains the API declaration of the theia plugin namespace
* /plugin-ext
Contains both the mechanisms for running plugins and providing them with an API namespace and the implementation of the ‘theia’ plugin API
* /plugin-ext-vscode
Contains an implementation of the vscode plugin API. Since vscode and theia API’s are largely compatible, the initialization basically just passes on the theia API and overrides a couple of members in the api object (plugin-ext-vscode/src/node/plugin-vscode-init.ts#33, etc.)
# Plugin API
* Theia plugin API is declared in a module called “@theiad/plugin” in a file plugin/theia.d.ts. This module provides pure declarations; no implementations for functions and classes are provided
* The implementation of the API defined in “@theia/plugin” is passed to plugin code by manipulating the module loading mechanism in plugin containers to construct an API module object. Plugin containers are node processes (plugin-ext/src/hosted/node/plugin-host.ts) and web workers (plugin-ext/src/hosted/browser/worker/worker-main.ts). This is done in the following places:
  * Browser: assign API object to Window[‘theia’] as plugin-ext/src/hosted/browser/worker/worker-main.ts#147
  * Back-end: override module load in plugin-ext/src/hosted/node/scanners/backend-init-theia.ts#42
# Remote procedure call API (main/ext)
* The plugin API is a local API for the plugin code to use: it is not designed to be a remote API and therefore the implementation of a particular API is responsible for communicating with the Theia instance running the plugin. For this purpose, a second set of API’s takes care of the communication between plugin process and Theia. This API is considered internal: only the implementation of the plugin API should use it. Let’s call it the main/ext API.
* This remote API is implemented by defining an interface and creating proxy objects that take care of marshalling a function call to a json message and on the other side reading the message and dispatching it to an implementation.
For an example of how to set this up, look for implementations of “LanguagesExt” and search in the code where the interface and the implementation are used.
* There is a convention to call interfaces that are to be implemented on the Theia side “<API Name>Main” and those implemented in the plugin “<API Name>Ext”. Usually, there is a pair of -Main and -Ext interfaces representing the both sides of  a set of related API functions.  For example the companion interface of “LanguagesExt” is “LanguagesMain”.
* No type information is used when sending object via RPC between plugin and theiad. Therefore, objects transferred through the remote API need to be pure dto objects: they cannot contain any methods.
