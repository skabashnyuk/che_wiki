### Overview

|Name|Language Server Features supported by Eclipse Che|Features covered by selenium tests|Features not covered by selenium tests|
| ------------- | ------------- | ---------- | ---------- |
|C#|autocomplete, find definition, code validation, code comment, rename, hover, signature help, go to symbol|autocomplete, code validation|find definition, code comment, rename, hover, signature help, go to symbol|
|PHP|autocomplete, find definition, code validation, code comment, rename, hover|autocomplete, code validation, find definition|code comment, rename, hover|
|Python|autocomplete, find definition, code validation, format, format selected code, code comment, rename, hover, find references, signature help, go to symbol|autocomplete, code validation, find definition, format|format selected code, code comment, rename, hover, find references, signature help, go to symbol|
|JSON|autocomplete, code validation, go to symbol, hover|code validation |autocomplete,  go to symbol, hover|
|Type script|autocomplete, find definition, code validation, format, code comment, rename, find references, signature help, go to symbol|autocomplete, code validation, find definition|format, code comment, rename, find references, signature help, go to symbol|
|Clang|autocomplete, find definition, code validation, format, format selected code, code comment, rename, signature help|autocomplete, code validation, find definition, format|format selected code, code comment, rename, signature help|
|Yaml|autocomplete, hover, code validation, code comment, go to symbol|autocomplete, hover, code validation, code comment|go to symbol|
|Camel| autocomplete, hover, diagnostic, go to symbol|autocomplete, hover| go to symbol|
|Golang|autocomplete, find definition, code validation, format, code comment, rename, hover, find references, signature help, go to symbol, find project symbol|autocomplete, find definition, code validation, format, hover| code comment, rename, find references, signature help, go to symbol, find project symbol|

### PHP language server
### Preconditions:

1. Create workspace from the **PHP** stack with **web-php-simple** project.
2. Enable **PHP** language server in the **Installers** tab and start the workspace.
3. Create "**index.php**" file with content:
``` php
<?php include 'lib.php';?>

<?php
echo sayHello("man");
?>

```
4. Create "**lib.php**" file with content:
``` php
<?php
function sayHello($name) {
    return "Hello, $name";
}
?>

```

### Testing process

* **Language server initialization**
1. From the project open "index.php" file.
2. Check ```Finished language servers initialization, file path '/web-php-simple/index.php'``` message in the **dev-machine** console.

* **Autocomplete feature**
1. Open "index.php" file.
2. Add a new line in line **5** and type ```$color = "blue";```.
3. Press **ENTER** button, type "$" and than **Ctrl**+**Space** buttons. The ```color``` fragment should be offered.
4. Delete the added lines

* **Find definition feature**
1. Open "index.php" file.
2. Set cursor to **4:10** position and invoke **Assistant** -> **Find Definition**. The "lib.php" file should be opened and **sayHello** function should be selected.
3. Close the "lib.php" file. Repeat previous step using F4 key instead of **Assistant** -> **Find Definition** invocation.

* **Code validation feature, Comment line**
1. Open "index.php" file.
2. Move cursor in **4:1** position.
3. Type any symbol there and check that error marker is appeared. Click on error marker - the proposal widget should be show ```; expected``` message. 
4. Restore content. Error marker should disappear.
5. Move cursor in line 4 position and comment this line by **Ctrl**+**/** buttons.
6. Check that text in line 4 was changed from ```echo sayHello("man");``` to ```//echo sayHello("man");```.
7. Uncomment this line by **Ctrl**+**/** buttons.

* **Hover feature**
1. Open "index.php" file.
2. Move mouse pointer on position **4:12**(sayHello() function).
3. Wait hover popup is appeared with text ```<?php function sayHello($name) {```.

**Find References**
1. Open "index.php" file.
2. Move mouse pointer on position **4:12**.
3. Start **Find References** feature by pressing **Alt**+**F7** buttons or from **Assistant** menu.
4. Check that **Find References** panel is opened with ```/web-php-simple/index.php From:4:6 To:4:14``` result in it.

**Signature Help**
1. Open "index.php" file.
2. Add a new line in position 5 and type ```sayHello```.
3. Type '(' symbol and wait for hover popup with ```(mixed $name)``` text.
4. Delete the added line

**Go To Symbol**
1. Open "lib.php" file.
2. Start **Go To Symbol** feature by **Ctrl**+**F12** buttons or from **Assistant** menu.
3. Wait for **Go To Symbol** form is opened with next line:
```
sayHello symbols(1)
```
4. Click on it and check that it correctly selected in file.

**Find Project Symbol**
1. Open "index.php" file.
2. Start **Find Project Symbol** feature by **Alt**+**N** buttons or from **Assistant** menu.
3. Type ```say``` in **Find Project Symbol** form input.
4. Wait for ```sayHello /web-php-simple/lib.php``` line.
5. Click on it and check that it correctly selected in file.


### Python language server
### Preconditions:

1. Create workspace from the **Python** stack with **console-python3-simple** project.
2. Enable **Python** language server in the **Installers** tab and start the workspace.
3. Create "**calc.py**" file with content:
``` python
import main.py

var2 = main.add(100, 200)

```
4. Create “**towers.py**” file with content:
``` python
def towers(i, start, finish, middle):
    if i > 0:
        towers(i-1, start, middle, finish)
        print('move disk from ', start, ' to ', finish)
        towers  ( i-1, middle, finish, start   )

towers  ( 5, 'X', 'Z', 'Y'      )
```
5. Create "**main.py**" with content:
``` python

class MyClass:
    var = 1
    variable = "variable"

    def function(self):
        print("This is a message inside the class.")


def add(a, b):
    return a + b
```
### Testing process

* **Language server initialization**

1. From the project open "main.py" file.
2. Check ``` Finished language servers initialization, file path '/console-python3-simple/main.py' ``` message in the **dev-machine** console.

* **Autocomplete feature**
1. Open "main.py" file.
2. In the last line type code fragment like ``` myobjectx = MyClass() ```.
3. Press **ENTER** button, type "myobjectx." and than **Ctrl**+**Space** buttons. Make sure that **function**, **var** and **variable** fields are available from the class in the proposal menu.
4. Delete added lines

* **Find definition feature**
1. Open "calc.py" file.
2. Set cursor to **3:15** position and invoke **Assistant** -> **Find Definition**. The "main.py" file should be opened and **add** function should be selected.
3. Close the "main.py" file. Repeat previous step using F4 key instead of **Assistant** -> **Find Definition** invocation.

* **Code validation feature, Comment line**
1. Open "calc.py" file.
2. Move cursor in **1:1** position.
3. Type any symbol there and check that error marker is appeared. Click on error marker - the proposal widget should be show ``` invalid syntax ``` message. 
4. Restore content. Error marker should disappear.
5. Add empty line in the end of file and press **SPACE** button. Make sure that warning marker with message: ``` W293 blank line contains whitespace ``` in line 4 is present.
6. Delete this line. The warning marker should disappear.
7. Move cursor in line 3 position and comment this line by **Ctrl**+**/** buttons.
8. Check that text in line 3 was changed from ``` var2 = main.add(100, 200) ``` to ``` #var2 = main.add(100, 200) ```.
9. Uncomment this line by **Ctrl**+**/** buttons.

* **Hover feature**
1. Open "main.py" file.
2. Move mouse pointer on position 6:12(print function).
3. Wait hover popup is appeared with text ``` Prints the values to a stream, of to sys.stdout by default ```.

* **Format code feature**
1. Open "towers.py" file.
2. Select all text on line 7.
3. Start **Format** option from context menu;
4. Check that the file content after formatting selected code was changed to:
```python
def towers(i, start, finish, middle):
    if i > 0:
        towers(i-1, start, middle, finish)
        print('move disk from ', start, ' to ', finish)
        towers  ( i-1, middle, finish, start   )


towers(5, 'X', 'Z', 'Y')

```
5. Start **Format** option from context menu again.
4. Check that the file content after full file formatting was changed to:
```python
def towers(i, start, finish, middle):
    if i > 0:
        towers(i-1, start, middle, finish)
        print('move disk from ', start, ' to ', finish)
        towers(i-1, middle, finish, start)


towers(5, 'X', 'Z', 'Y')

```

**Rename**
1. Open "main.py" file.
2. Select "var" variable.
3. Start **Rename** feature by **Shift+F6** or from **Assistant** menu.
4. Type new variable name.
5. Check that the variable name was changed.

**Find References**
1. Open "calc.py" file.
2. Select ```var2``` variable.
2. Start **Find References** feature by pressing **Alt**+**F7** buttons or from **Assistant** menu.
3. Check that Find References panel is opened with ```/console-python3-simple/calc.py From:3:0 To:3:5``` result in it.

**Signature Help**
1. Open "calc.py" file.
2. Type ``` main.add ``` on line 4.
3. Type '(' symbol and wait for hover popup with ``` add(a,b) ``` text.
4. Delete added line

**Go To Symbol**
1. Open "main.py" file.
2. Start **Go To Symbol** feature by **Ctrl**+**F12** buttons or from **Assistant** menu.
3. Wait for **Go To Symbol** form is opened with next lines:
```
MyClass symbols(5)
var
variable
function
add
```
4. Click on any of them and check that it correctly selected in file.


### JSON language server
### Preconditions:

1. Create workspace from the **Node** stack with **nodejs-hello-world** project.
2. Enable **JSON** language server in the **Installers** tab and start the workspace.

### Testing process

* **Language server initialization**
1. From the project open "package.json" file.
2. Check ```Finished language servers initialization, file path '/nodejs-hello-world/package.json'``` message in the **dev-machine** console.

* **Code validation feature**
1. Open "package.json" file.
2. Remove `,` symbol in line **8**. Make sure that error marker appears. Click on the marker and check message like `Expected '(end)' and instead saw ':'.`in the proposal window. 
3. Hover mouse on "author" text and wait for hover popup with ```Expected comma or closing brace``` text. Return the just deleted coma and wait disappearance of the marker. 
4. Go to the line **9** and add fragment like: `"newObj":[1,2,3],`. Make sure that json file does not have any errors.
5. Add this object again and check error marker with ```Duplicate object key``` message. Delete just add object and check wait disappearance of the marker.
6. Go to the line **6** and press **ENTER**. Add `"newObj":[1,2,3],` object and check there is not any errors.

* **Go To Symbol**
1. Open "package.json" file.
2. Start **Go To Symbol** feature by **Ctrl**+**F12** buttons or from **Assistant** menu.
3. Wait for **Go To Symbol** form is opened with next lines:
```
name symbols(10)
version
description
main
scripts
test
author
license
dependencies
express
```
4. Click on any of them and check that it correctly selected in file.



### Clang language server
### Preconditions:

1. Create workspace from the **C++** stack with **console-cpp-simple** project.
2. Enable **Clangd** language server in the **Installers** tab and start the workspace.
3. Create "**hello.cc**" file with content:
``` cpp
#include <iostream>
 
int main()
{
  std::cout << "Hello World!" << std::endl;
  return 0;
}

```
4. Create “**iseven.h**” file with content:
``` cpp
#ifndef VARIABLE
#define VARIABLE

int isEven(int arg);

#endif

```
5. Create "**iseven.cpp**" with content:
``` cpp
                  int isEven(int x)     {
    return x % 2 ==               0;
                    }

```

6. Create "**hello.cpp**" with content:
``` cpp
#include <iostream>
#include "iseven.h"

void test(int);

int main()
{
    int x   =   4;
  std::cout << "Hello World!" << std::endl;
  std::cout << isEven(x) << std::endl;
  return 0;
}

```

### Testing process

* **Language server initialization**

1. From the project open "hello.cc" file.
2. Check ```Finished language servers initialization, file path '/console-cpp-simple/hello.cc``` message in the **dev-machine** console.

* **Code validation feature, Autocomplete feature**
1. Open "hello.cc" file.
2. Add a new line in line 6. Type `std::`. Make sure that error marker with ```expected unqualified-id``` message appears. 
3. Type ```std::cou``` and launch code assistant by Ctrl+Space. Select ```cout outstream``` from the proposal menu. Type ```<< "Hello World!;"``` Make sure that there is no any errors. 
4. Erase ```std::```. Make sure that error marker appears in line 6. Add ```using namespace std;```in the line 2. 5. Make sure that there is no any errors.

* **Find definition feature**
1. Open "hello.cpp" file.
2. Set cursor to **10:20** position and invoke **Assistant** -> **Find Definition**. The "iseven.h" file should be opened and **add** function should be selected.
3. Close the "iseven.h" file. Repeat previous step using F4 key instead of **Assistant** -> **Find Definition** invocation.

* **Comment line**
1. Open "hello.cc" file.
2. Move cursor in line 5 position and comment this line by Ctrl+/ buttons.
3. Check that text in line 3 was changed from ```  std::cout << "Hello World!" << std::endl;``` to ```//  std::cout << "Hello World!" << std::endl;```.
4. Uncomment this line by Ctrl+/ buttons.

* **Format code feature**
1. Open "hello.cpp" file.
2. Select all text on line 8.
3. Start **Format** option from context menu in the Editor;
4. Check that the file content after formatting selected code was changed to:
```cpp
  int x = 4;
```
5. Open "iseven.cpp" file.
6. Start **Format** option from context menu.
7. Check that the file content after full file formatting was changed to:
```cpp
int isEven(int x) { return x % 2 == 0; }
```

**Rename**
1. Open "hello.cpp" file.
2. Select "x" variable.
3. Start **Rename** feature by **Shift+F6** or from **Assistant** menu.
4. Type new variable name.
5. Check that the variable name was changed.

**Signature Help**
1. Open "hello.cpp" file.
2. Add a new line in line 8 and type ```isEven```.
3. Type '(' symbol and wait for hover popup with ```isEven(int arg)->int``` text.
4. Delete added line.


### TypeScript language server
### Preconditions:

1. Create workspace from the **Node** stack with **nodejs-hello-world** project.
2. Enable **TypeScript** language server in the **Installers** tab and start the workspace.
3. Create “**Greeter.ts**” file with content:
```typescript
import {Print} from './testPrint'

class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
    
     testPrint(): void {
        const printVar = new Print();
        printVar.print("test print");
    }
}

let greeter = new Greeter("world");

```
4. Create "**testPrint.ts**" with content:
```typescript
let name: string;
export class Print {

print (setVAlue: string): void 

{
    name = setVAlue;
    console.log('<<:'+ name);
}     
    
}
```

### Testing process

* **Language server initialization**

1. From the project open "Greeter.ts" file.
2. Check ```Finished language servers initialization, file path '/nodejs-hello-world/Greeter.ts'``` message in the **dev-machine** console.

* **Autocomplete feature**
1. Open "Greeter.ts" file.
2. Add empty line after the code and type ```greeter.```. Sent **Ctrl**+**Space**. Make sure that ```greet``` function and ```greeting``` field are present in the proposal panel.
3. Delete the added line.

* **Find definition feature**
1. Open "Greeter.ts" file.
2. Set cursor to **14:20** position and invoke **Assistant** -> **Find Definition**. The "testPrint.ts" file should be opened and **print** function should be selected.
3. Close the "testPrint.ts" file. Repeat previous step using **F4** key instead of **Assistant** -> **Find Definition** invocation.

* **Code validation feature, Comment line**
1. Open "Greeter.ts" file.
2. Move cursor in **3:2** position.
3. Add space into keyword class like: ```c lass```. Make sure that error markers have appeared. Click on first marker and check the message like: ```Cannot find name 'lass'.```.
4. Restore content. Error marker should disappear.
7. Move cursor in line 1 position and comment this line by **Ctrl**+**/** buttons.
8. Check that text in line 1 was changed from ```import {Print} from './testPrint'``` to ```//import {Print} from './testPrint'```.
9. Uncomment this line by **Ctrl**+**/** buttons.

* **Format code feature**
1. Open "testPrint.ts" file.
2. Start **Format** option from context menu;
4. Check that the file content after formatting was changed to:
```typescript
let name: string;
export class Print {

    print(setVAlue: string): void {
        name = setVAlue;
        console.log('<<:' + name);
    }

}

```

**Rename**
1. Open "Greeter.ts" file.
2. Select ```printVar``` variable.
3. Start **Rename** feature by **Shift+F6** or from **Assistant** menu.
4. Type new variable name.
5. Check that the variable name was changed.

**Find References**
1. Open "Greeter.ts" file.
2. Move mouse pointer on position **4:12**.
3. Start **Find References** feature by pressing **Alt**+**F7** buttons or from **Assistant** menu.
4. Check that **Find References** panel is opened with ```/nodejs-hello-world/Greeter.ts From:4:5 To:4:13``` result in it.

**Signature Help**
1. Open "Greeter.ts" file.
2. Add empty line after the code and type ```greeter.testPrint```. 
3. Type '(' symbol and wait for hover popup with ```testPrint(): void``` text.
4. Delete added line.

**Go To Symbol**
1. Open "Greeter.ts" file.
2. Start **Go To Symbol** feature by **Ctrl**+**F12** buttons or from **Assistant** menu.
3. Wait for **Go To Symbol** form is opened with next lines:
```
"Greeter" symbols(9)
greeter
Greeter
constructor
greet
greeting
testPrint
printVar
Print
```
4. Click on any of them and check that it correctly selected in file.

**Find Project Symbol**
1. Open "Greeter.ts" file.
2. Start **Find Project Symbol** feature by **Alt**+**N** buttons or from **Assistant** menu.
3. Type ```print``` in **Find Project Symbol** form input.
4. Wait for ```testPrint /nodejs-hello-world/Greeter.ts``` line.
5. Click on it and check that it correctly selected in file.


### Yaml language server
### Preconditions:

1. Create workspace from the **Node** stack with "**nodejs-hello-world**" project.
2. Enable **Yaml** language server in the **Installers** tab.
3. Start workspace. Set the **YAML** schema: 
    - Menu **Profile** -> **Preferences**;
    - Select **Yaml**->**Add Schema URl** button -> type ```kubernetes```. 
3. Create "**openshift.yaml**".
4. Create “**deployment.yaml**” file with content:
```
apiVersion: v1
kind: DeploymentConfig
metadata:
  annotations:
    openshift.io/generated-by: OpenShiftNewApp
  creationTimestamp: '2018-07-17T11:11:50Z'
  generation: 4
  labels:
    app: che
    template: che
  name: che
  namespace: eclipse-che
  resourceVersion: '9713'
  selfLink: /apis/apps.openshift.io/v1/namespaces/eclipse-che/deploymentconfigs/che
  uid: 33bda3fd-89b2-11e8-be77-8c1645547d72
spec:
  replicas: 1
  revisionHistoryLimit: 2
  selector:
    app: che
  strategy:
    activeDeadlineSeconds: 21600
    recreateParams:
      timeoutSeconds: 600
    resources: {}
    type: Recreate
  template:
    metadata:
      annotations:
        openshift.io/generated-by: OpenShiftNewApp
      creationTimestamp: "null"
      labels:
        app: che
    spec:
      containers:
        - env:
            - name: CHE_CONF
              value: /home/user/che-conf
            - name: CHE_IMAGE_REPO
              value: eclipse/che-server
            - name: CHE_IMAGE_TAG
              value: nightly
            - name: CHE_INFRASTRUCTURE
              value: openshift
            - name: CHE_INFRA_KUBERNETES_MASTER__URL
              value: 'https://172.0.0.1:8443'
            - name: CHE_LOCAL_CONF_DIR
              value: /home/user/che-conf
            - name: CHE_MULTIUSER
              value: 'false'
            - name: CHE_OPENSHIFT_PROJECT
              value: eclipse-che
            - name: OPENSHIFT_KUBE_PING_NAMESPACE
              valueFrom:
                fieldRef:
                  apiVersion: v1
                  fieldPath: metadata.namespace
            - name: NAMESPACE
              valueFrom:
                fieldRef:
                  apiVersion: v1
                  fieldPath: metadata.namespace
            - name: CHE_HOST
              value: 'che-${NAMESPACE}.172.0.0.1.nip.io'
            - name: CHE_PORT
              value: '8080'
            - name: CHE_API
              value: 'http://che-${NAMESPACE}.172.0.0.1.nip.io/api'
            - name: CHE_WEBSOCKET_ENDPOINT
              value: 'ws://che-${NAMESPACE}.172.0.0.1.nip.io/api/websocket'
            - name: CHE_DEBUG_SERVER
              value: 'false'
            - name: CHE_INFRASTRUCTURE_ACTIVE
              value: openshift
            - name: CHE_INFRA_KUBERNETES_BOOTSTRAPPER_BINARY__URL
              value: >-
                http://che-${NAMESPACE}.172.0.0.1.nip.io/agent-binaries/linux_amd64/bootstrapper/bootstrapper
            - name: CHE_INFRA_KUBERNETES_MACHINE__START__TIMEOUT__MIN
              value: '5'
            - name: CHE_INFRA_KUBERNETES_OAUTH__TOKEN
            - name: CHE_INFRA_KUBERNETES_USERNAME
            - name: CHE_INFRA_KUBERNETES_PASSWORD
            - name: CHE_INFRA_OPENSHIFT_PROJECT
              value: eclipse-che
            - name: CHE_INFRA_KUBERNETES_PVC_STRATEGY
              value: unique
            - name: CHE_INFRA_KUBERNETES_PVC_PRECREATE__SUBPATHS
              value: 'false'
            - name: CHE_INFRA_OPENSHIFT_TLS__ENABLED
              value: 'false'
            - name: CHE_INFRA_KUBERNETES_TRUST__CERTS
              value: 'false'
            - name: CHE_LOGS_DIR
              value: /data/logs
            - name: CHE_LOG_LEVEL
              value: INFO
            - name: CHE_KEYCLOAK_AUTH__SERVER__URL
              value: '${PROTOCOL}://keycloak-${NAMESPACE}.${ROUTING_SUFFIX}/auth'
            - name: CHE_INFRA_OPENSHIFT_OAUTH__IDENTITY__PROVIDER
              value: 'NULL'
            - name: CHE_PREDEFINED_STACKS_RELOAD__ON__START
              value: 'true'
            - name: JAVA_OPTS
              value: >-
                -XX:MaxRAMFraction=2 -XX:+UseParallelGC -XX:MinHeapFreeRatio=10
                -XX:MaxHeapFreeRatio=20 -XX:GCTimeRatio=4
                -XX:AdaptiveSizePolicyWeight=90 -XX:+UnlockExperimentalVMOptions
                -XX:+UseCGroupMemoryLimitForHeap
                -Dsun.zip.disableMemoryMapping=true -Xms20m
            - name: CHE_WORKSPACE_AUTO_START
              value: 'false'
            - name: CHE_INFRA_KUBERNETES_PVC_QUANTITY
              value: 1Gi
            - name: PROTOCOL
              value: http
            - name: ROUTING_SUFFIX
              value: 172.19.20.234.nip.io
            - name: OPENSHIFT_IDENTITY_PROVIDER_CERTIFICATE
              valueFrom:
                secretKeyRef:
                  key: ca.crt
                  name: openshift-identity-provider
                  optional: true
            - name: CHE_WORKSPACE_PLUGIN__REGISTRY__URL
              value: 'NULL'
          image: 'eclipse/che-server:latest'
          imagePullPolicy: Always
          livenessProbe:
            failureThreshold: 3
            httpGet:
              path: /api/system/state
              port: 8080
              scheme: HTTP
            initialDelaySeconds: 50
            periodSeconds: 10
            successThreshold: 1
            timeoutSeconds: 2
          name: che
          ports:
            - containerPort: 8080
              name: http
              protocol: TCP
          readinessProbe:
            failureThreshold: 5
            httpGet:
              path: /api/system/state
              port: 8080
              scheme: HTTP
            initialDelaySeconds: 25
            periodSeconds: 10
            successThreshold: 1
            timeoutSeconds: 5
          resources:
            limits:
              memory: 1Gi
            requests:
              memory: 256Mi
          terminationMessagePath: /dev/termination-log
          terminationMessagePolicy: File
          volumeMounts:
            - mountPath: /data
              name: che-data-volume
      dnsPolicy: ClusterFirst
      restartPolicy: Always
      schedulerName: default-scheduler
      securityContext: {}
      serviceAccount: che
      serviceAccountName: che
      terminationGracePeriodSeconds: 360
      volumes:
        - name: che-data-volume
          persistentVolumeClaim:
            claimName: che-data-volume
  test: false
  triggers:
    - type: ConfigChange
status:
  availableReplicas: 1
  conditions:
    - lastTransitionTime: '2018-07-17T12:49:00Z'
      lastUpdateTime: '2018-07-17T12:49:00Z'
      message: Deployment config has minimum availability.
      status: 'True'
      type: Available
    - lastTransitionTime: '2018-07-17T12:47:37Z'
      lastUpdateTime: '2018-07-17T12:49:29Z'
      message: replication controller "che-4" successfully rolled out
      reason: NewReplicationControllerAvailable
      status: 'True'
      type: Progressing
  details:
    causes:
      - type: ConfigChange
    message: config change
  latestVersion: 4
  observedGeneration: 4
  readyReplicas: 1
  replicas: 1
  unavailableReplicas: 0
  updatedReplicas: 1

```

### Testing process

* **Language server initialization**
1. From the project open "openshift.yml" file.
2. Check ``` Finished language servers initialization, file path '/nodejs-hello-world/openshift.yaml' ``` message in the **dev-machine** console.

* **Autocomplete feature**
1. From the project open "openshift.yml" file.
1. In the opened file launch autocomplete (**Ctrl**+**Space**). Make sure that ```kind``` value is present in the proposal widget, check document window with content:``` Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: http://releases.k8s.io/HEAD/docs/devel/api-conventions.md#types-kinds. ``` Enter this value.
2. Launch autocomplete, select ``` PersistentVolume ```. Make sure that there is no errors.
3. Go to the new line type ``` api ```, launch autocomplete, make sure that ``` apiVersion: ``` has been passed. Launch autocomplete, ``` v1 ``` value should be added.
4. Go to the new line and type ``` me ```. Launch autocomplete and check that ``` metadata: ``` should be added.

* **Code validation feature, Comment line**
1. Open "deployment.yaml" file.
2. Add **'a'** symbol to **1:1** position and check that error marker is appeared. 
3. Click on the error marker and check ```Unexpected property aapiVersion``` message.
4. Restore content. Error marker should disappear. 

* **Hover feature**
1. Open "deployment.yaml" file.
2. Move mouse pointer on 'kind:' text in line **2**, wait hover popup and check ``` Kind is a string value representing the REST resource this object represents. ``` message in it.
3. Move mouse pointer on 'apiVersion:' text in line **1**, wait hover popup and check ``` APIVersion defines the versioned schema of this representation of an object. ``` message in it.

* **Comment code feature:**
1. Select any line of code.
2. Comment this line by **Ctrl**+**/** buttons and check that the line is commented.
3. Launch comment feature again and check that the line uncommented.

**Go To Symbol**
1. Open "deployment.yaml" file.
2. Start **Go To Symbol** feature by **Ctrl**+**F12** buttons or from **Assistant** menu.
3. Wait for **Go To Symbol** form is opened with next lines:
```
apiVersion symbols(194)
kind
metadata
annotations
openshift.io/generated-by
creationTimestamp
generation
labels
app
```
4. Click on any of them and check that it correctly selected in file.



### Apache Camel language server
### Preconditions:

1. Create workspace from the **Apache Camel based projects** stack.
2. Enable **Apache Camel** language server in the **Installers** tab and start the workspace.
3. Create a project.
4. Create "**camel.xml**" file with content:
``` xml
<!-- here we have Spring XML file with all the namespaces here in the top of the XML file -->
<beans xmlns="http://www.springframework.org/schema/beans"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:camel="http://camel.apache.org/schema/spring"
  xmlns:cxf="http://camel.apache.org/schema/cxf"
  xsi:schemaLocation="
         http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
         http://camel.apache.org/schema/spring http://camel.apache.org/schema/spring/camel-spring.xsd
         http://camel.apache.org/schema/cxf http://camel.apache.org/schema/cxf/camel-cxf.xsd">

  <!-- this is Spring XML example of the Camel route in the ReportIncidentRoutes class -->
  <!-- this is for demonstration purpose, to show how you can use Camel with XML DSL -->

  <!-- here we define the CXF endpoint, where {{port}} refers to a placeholder so we can define the port number
          in an external .properties file -->
  <cxf:cxfEndpoint id="reportIncident"
    address="http://localhost:{{port}}/camel-example-reportincident/webservices/incident"
    wsdlURL="etc/report_incident.wsdl"
    serviceClass="org.apache.camel.example.reportincident.ReportIncidentEndpoint"/>

  <!-- We use a bean to make the response bean that CXF expects -->
  <bean id="responseBean" class="org.apache.camel.example.reportincident.MyBean"/>

  <!-- this is the bean we use to generate the dynamic file name -->
  <bean id="filenameGenerator" class="org.apache.camel.example.reportincident.FilenameGenerator"/>

  <!-- this CamelContext contains the equivalent route from the Java DSL, but in XML
       so end users can see how to implement the route in both Java and XML -->
  <camelContext id="camel" xmlns="http://camel.apache.org/schema/spring">

    <!-- property which contains port number -->
    <!-- we have file:target/custom.properties which can be optional and override existing values, we use this for testing purpose -->
    <camel:propertyPlaceholder id="properties" location="classpath:incident.properties,file:target/custom.properties"/>

    <!-- this is the first route that uses CXF as web service -->
    <route>
      <from uri="tim"/>
      <convertBodyTo type="org.apache.camel.example.reportincident.InputReportIncident"/>
      <setHeader headerName="CamelFileName">
        <method bean="filenameGenerator" method="generateFilename"/>
      </setHeader>
      <to uri="velocity:etc/MailBody.vm"/>
      <to uri="file://target/subfolder"/>
      <transform>
        <method bean="responseBean" method="getOK"/>
      </transform>
    </route>

    <!-- this is the 2nd route that pickup files and send them as emails -->
    <route>
      <from uri="file://target/subfolder"/>
      <setHeader headerName="subject">
        <constant>new incident reported</constant>
      </setHeader>
      <to uri="smtp://someone@localhost?password=secret&amp;to=incident@mycompany.com"/>
    </route>

  </camelContext>

</beans>

```
### Testing process

* **Language server initialization**

1. From the project open "camel.xml" file.
2. Check ``` Finished language servers initialization, file path '/web-java-spring/camel.xml' ``` message in the **dev-machine** console.

* **Autocomplete feature**
1. Open "camel.xml" file.
2. Move to **37:21** position and invoke **Ctrl** + **Space**. Check that ``` timer:timerName ``` text fragment was added.
3. Hover mouse pointer on the added fragment and check that next text ``` The timer component is used for generating message exchanges when a timer fires. ``` is present. 
4. Type ```?```. Invoke codeassistant again by **Ctrl** + **Space** and select '``fixedRate''' proposal. Make sure that ``` fixedRate=false ``` fragment has been pasted properly.
5. Type ``` &amp; ```. Invoke **codeassistant**, select ``` exchangePatterninto ``` proposal menu. Invoke **Ctrl** + **Space** again. Paste ``` InOnly ``` param.
6. Check that content of line 37 is ```       <from uri="timer:timer:timerName?fixedRate=false&amp;exchangePattern=InOnly"/> ```

* **Hover feature**(depends on Autocomplete step)
1. Open "camel.xml" file.
2. Move mouse pointer on position **37:26**.
3. Wait hover popup is appeared with text ``` The timer component is used for generating message exchanges when a timer fires. ```.

* **Go To Symbol**
1. Open "camel.xml" file.
2. Start **Go To Symbol** feature by **Ctrl**+**F12** buttons or from **Assistant** menu.
3. Wait for **Go To Symbol** form is opened with next lines:
```
<no id> symbols[2]
<no id>
```
4. Click on any of them and check that it correctly selected in file.



### Golang language server
### Preconditions:

1. Create workspace from the **Go** stack with **desktop-go-simple** project.
2. Enable **Golang** language server in the **Installers** tab and start the workspace.
3. Create "**format.go**" file with content:
``` go
package
main

import (

	   "fmt"
	"math"

)

func    print(   ) {
	   fmt.Printf("Hello, world. Sqrt(2) = %v\n",  math.Sqrt(2))
}

```
4. Create "**main.go**" file with content:
``` go

package main

import (
	"fmt"
	"math"
)

func main() {
	fmt.Printf("Hello, world. Sqrt(2) = %v\n", math.Sqrt(2))
}

```
5. Create "**print.go**" file with content:
``` go
package main

import (
	"fmt"
)

const COLOR_RED = "\x1b[31;1m "
const COLOR_GREEN = "\x1b[32;1m "
const COLOR_YELLOW = "\x1b[33;1m "
const COLOR_BLACK = "\x1b[34;1m "

func Print(color string, s string) {
	fmt.Printf("%s %s\n", color, s)
}

```
6. Create "**towers.go**" file with content:
``` go
package main

import (
	"fmt"
)

var count int

func hanoi(n int, a, b, c string) {
	if n == 1 {
		count++
		Print(COLOR_GREEN, fmt.Sprintf("Step %d: move disk from %s to %s\n", count, a, c))
		return
	}

	hanoi(n-1, a, c, b)
	count++
	Print(COLOR_YELLOW, fmt.Sprintf("Step %d: move disk from %s to %s\n", count, a, c))
	hanoi(n-1, b, a, c)
}

func main() {
	hanoi(3, "1", "2", "3")
}

```

### Testing process

* **Language server initialization**
1. From the project open "main.go" file.
2. Check ```Finished running tool: /usr/local/go/bin/go build``` message in the **dev-machine** console.

* **Autocomplete feature**
1. Open "main.go" file.
2. Create a new line on line 10.
3. Add `fmt.P` code and launch autocomplete by Ctrl+Space.
4. Check that proposal `Printf`is present.
5. Delete created line.

* **Find definition feature**
1. Open "towers.go" file.
2. Set cursor to 12:5 position and invoke **Assistant** -> **Find Definition**. The "print.go" file should be opened and function `Print` should be selected.
3. Close the `print.go` file. And repeat previous step using F4 key instead of **Assistant** -> **Find Definition** invocation.

* **Code validation feature, Comment line**
1. Open "main.go" file.
2. Move cursor in **1:1** position.
3. Type `p` symbol there and check that error marker is appeared. Click on error marker - the proposal widget should be show ```expected 'package', found 'IDENT' ppackage``` message. 
4. Restore content. Error marker should disappear.
5. Move cursor in line 1 position and comment this line by **Ctrl**+**/** buttons.
6. Check that text in line 3 was changed from ```package main``` to ```//package main```.
7. Uncomment this line by **Ctrl**+**/** buttons.

* **Hover feature**
1. Open "towers.go" file.
2. Move mouse pointer on position **12:15**
3. Wait hover popup is appeared with text ```const COLOR_YELLOW string = "\x1b[33;1m "```.

* **Format code feature**
1. Open "format.go" file.
2. Start **Format** option from context menu;
3. Check that the file content was changed to:
```go
package main

import (
	"fmt"
	"math"
)

func print() {
	fmt.Printf("Hello, world. Sqrt(2) = %v\n", math.Sqrt(2))
}

```

**Rename**
1. Open "towers.go" file.
2. Select "n" variable in line **10**.
3. Start **Rename** feature by **Shift**+**F6** or from **Assistant** menu.
4. Type new variable name.
5. Check that the variable name was changed.

**Find References**
1. Open "towers.go" file.
2. Select ```count``` variable
2. Start **Find References** feature by pressing **Alt**+**F7** buttons or from **Assistant** menu.
3. Check that Find References panel is opened with ```/desktop-go-simple/towers.go From:7:5 To:7:10``` result in it.

**Signature Help**
1. Open "towers.go" file.
2. Type ```hanoi``` on line 24.
3. Type '(' symbol and wait for hover popup with ```hanoi(n int, a, b, c string)``` text.
4. Delete added line.

**Go To Symbol**
1. Open "towers.go" file.
2. Start **Go To Symbol** feature by **Ctrl**+**F12** buttons or from **Assistant** menu.
3. Wait for **Go To Symbol** form is opened with next lines:
```
main symbols(4)
count
hanoi
main
```
4. Click on any of them and check that it correctly selected in file.

**Find Project Symbol**
1. Open "towers.go" file.
2. Start **Find Project Symbol** feature by **Alt**+**N** buttons or from **Assistant** menu.
3. Type ```Print``` in **Find Project Symbol** form input.
4. Wait for ```Print /desktop-go-simple/print.go``` line.
5. Type ```hanoi``` in **Find Project Symbol** form input.
6. Wait for ```hanoi /desktop-go-simple/towers.go``` line.
7. Click on any of them and check that it correctly selected in file.


### C# language server

### Preconditions:

1. Create workspace from the **.NET** stack with **.NET** project.
2. Enable **C#** language server in the **Installers** tab and start the workspace.

### Testing process

* **Language server initialization**
1. From the project open "Program.cs" file.
2. Check ```Finished language servers initialization, file path '/dotnet-web-simple/Program.cs'``` message in the **dev-machine** console.

* **Code validation feature, Comment line, Autocomplete feature**
1. Open "Program.cs" file.
2. Make sure that code is validated by LS. We should have info markers in the 1-5 and 8,9 positions. Hover curso for instance on the first maker. Make sure that hint contains ```Unnecessary using directive```.
3. Remove ```;``` from the ```Build();``` - the error marker should appear. Undo changes the error marker should disappear. 
4. Remove ```Build``` till ```.``` symbol. Invoke autocomplete (Ctrl+Space). Make sure that ```Build``` is present in the widget. 
5. Hover cursor on ```Build```. Make sure that docker window with ```Builds an Microsoft.AspNetCore.Hosting.IWebHost which hosts a web application.``` has been opened.
6. Paste ```Build``` and complete ```Build()```;
7. Move cursor in line 1 position and comment this line by **Ctrl**+**/** buttons.
8. Check that text in line 3 was changed from ```package main``` to ```//package main```.
9. Uncomment this line by **Ctrl**+**/** buttons.

* **Find definition feature**
1. Open "Startup.cs" file.
2. Add new method in the body of ```Startup``` class:
```
public static String checkMessage(){
            return "Message has been checked";
        }
```
3. Add instance of the ```Startup.cs``` class into ```Program.cs``` in next way:
set cursor into the body of Main method of Program.cs and create invocation like:
```Startup.checkMessage();```
4. Set cursor on the ```checkMessage``` and invoke go to the definition by F4
Make sure that Startup.cs file is opened and cursor has been placed to checkMessagemethod.
5. Set cursor to ```Build();``` and invoke the go to the definition again. Make sure that ```IWebHostBuilder``` has been opened and cursor was set to the Build position (Clarify this usecase because this feature may be unavailable)

* **Hover feature**
1. Open "Program.cs" file.
2. Hover cursor on ```Build```. Make sure that hovering works without duplicated items. In the widget we should get next: ```IWebHost IWebHostBuilder.Build() Builds an Microsoft.AspNetCore.Hosting.IWebHost which hosts a web application.```

**Rename**
1. Open "Program.cs" file.
2. Select "" variable in line ****.
3. Start **Rename** feature by **Shift**+**F6** or from **Assistant** menu.
4. Type new variable name.
5. Check that the variable name was changed.

**Signature Help** TODO
1. Open "Program.cs" file.
2. Type `````` on line .
3. Type '(' symbol and wait for hover popup with `````` text.
4. Delete added line.

**Go To Symbol** TODO
1. Open "Program.cs" file.
2. Start **Go To Symbol** feature by **Ctrl**+**F12** buttons or from **Assistant** menu.
3. Wait for **Go To Symbol** form is opened with next lines:
```

```
4. Click on any of them and check that it correctly selected in file.

### TODO
* Maven LS in progress ...
* Testcases with sidecars - clarify what do we need ?
* Add next use cases to LS that can format selected text:
    * there is no blank line in selected text
    * there is a blank line in selected text
    * there are several lines in selected text
    * cursor position must be in the same place after formatting

**The plan is not complete and should be supplemented**
