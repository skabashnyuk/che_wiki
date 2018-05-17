
1. **PHP language server:**
* Create a workspace through Dashboard based on Default PHP stack. Enable PHP language server by slider on dashboard if needed.
* Go to freshly created workspace and create **_web-php-simple_** project with wizard
* Open **_index-php_** file and make sure that language server has been initialized. Go to the _**dev-machine**_ console and check message like: `2018-04-23 08:47:03,059[rverInitializer]  [INFO ] [.a.l.LanguageServerInitializer 216]  - Initialized language server 'org.eclipse.che.plugin.php.languageserver'`
* Add an error in the `echo` command and check that error marker is appeared. Click on error marker - the proposal tooltip should pop up. Restore content. Error marker should disappear.
* Add variable like `$color = "blue";`. Make sure there are no errors. Go to the end of `echo "Hello World!"` type `$` and launch autocompletion by Ctrl+Space. The `color` fragment should be offered.
* Set cursor to the new line type `e` and launch autocompletion by Ctrl+Space. Check that proposal is present, see link below:
[PHP autocoplete proposal](https://www.dropbox.com/s/2hrzg04hqbz1a4j/Selection_012.png?dl=0)
* Create a file in the current project with name `lib.php`. Add next content into the file:
```php
<?php

function sayHello($name) {
    return "Hello, $name";
}
?>
```
* Add into the `index.php` file next expression: `echo sayHello("man");`
* Set cursor to `sayHello` and Assistant -> Find Definition. Make sure, that `lip.php` file is opened and function `sayHello`is selected.
* Close the `lib.php` file and open `index.php`. Set cursor to `sayHello` and press F4, `lip.php` file should be opened and function `sayHello` should be selected.

2. **Python language server:**
* Create a workspace through Dashboard based on Default python stack. Enable language server by slider on dashboard  if it needed.
* Go to a freshly created workspace and create _**console-python3.5-simple**_. Open the `main.py`file and make sure that language server has been initialized. Go to the _**dev-machine**_ console and check message like: `2018-04-24 13:24:49,159[rverInitializer]  [INFO ] [.a.l.LanguageServerInitializer 216]  - Initialized language server 'org.eclipse.che.plugin.python.languageserver`
* Add an error in the `print` command and check that error marker is appeared. Click on error marker - the proposal widget should be show `invalid syntax` message. Restore content. Error marker should disappear.
type. Remove content from the file and paste code like:
```python 
class MyClass:
    var = 1
    variable = "bla"

    def function(self):
        print("This is a message inside the class.")
```

Add empty line. Make sure that warning marker with message: `W293 blank line contains whitespace` is present
* Add empty line again and type code fragment like `myobjectx = MyClass()`
* Press enter and type `myobjectx.` than ctrl+space. Make sure that `function`, `var` and `variable` fields are available from the class in the proposal menu.
* Create new python file for instance with name `myModule.py` and add simple content like:
```python
def add(a, b):
    return a + b
```
Close the just created file. Open myClass and add next expression: 
```pyhon
var2 = myModule.add(100, 200)
```
* Set cursor to `add` and invoke Assistant -> Find Definition. The `myModule.py` file should be opened and function `add` should be selected
* Close the `myModule.py` file. And repeat previous step using F4 key instead of Assistant -> Find Definition invocation

3. **JSON language server:**
* Create a workspace through Dashboard based on Default Node Stack. Enable JSON language server by slider on dashboard  if it need.
* Go to the just created workspace and create _**nodejs-hello-world**_. Open `package.json`file and make sure that language server has been initialized. Go to the _**dev-machine**_ console and check message like: `2018-04-23 13:00:27,948[rverInitializer]  [INFO ] [.a.l.LanguageServerInitializer 109]  - Started language servers initialization, file path '/nodeJs/package.json'`
* Remove `,` symbol after last brace 
```
{
  "name": "nodejs-sample",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
``` 
Make sure that error marker appears. Click on the marker and check message like `Expected '(end)' and instead saw ':'.`in the proposal window. Return the just deleted coma and wait disappearance the marker. Go to the line 9 and add fragment like: `"newObj":[1,2,3],`. Make sure that JSON does not have any errors.

4. **Type script language server:**
* Create a workspace through Dashboard based on Default Node Stack. Enable TypeScript language server by slider on dashboard  if it need.
* Go to the just created workspace and create _**nodejs-hello-world**_. Create for example `greeter.ts` file and  add next content:
```typescript
class Greeter {
    constructor(public greeting: string) { }
    greet() {
        return "<h1>" + this.greeting + "</h1>";
    }
};

var greeter = new Greeter("Hello, world!");
    
document.body.innerHTML = greeter.greet();
```
make sure that language server has been initialized. Go to the _**dev-machine**_ console and check message like: `[INFO ] [.a.l.LanguageServerInitializer 216]  - Initialized language server 'org.eclipse.che.plugin.web.typescript`.
Add new file like: `Greeter.ts` wit next content: 
```typescript
class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
}

let greeter = new Greeter("world");
```
* Add space into keyword `class` like: `c lass`. Make sure that error markets have appear. Click on first marker and check the message like: `cannot find lass`
* Remove the space - error makers should disappear. Add empty line after the code and type `greeter.`. Sent ctrl+space. Make sure that `greet()` function and `greeting` field are present in the proposal panel.
* Create new file with name `printTest.ts` and add next content:
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
* Close the just created file 
* Open greeter.ts  and add to first line: `import {Print} from './printTest'`
* Set cursor after `greet()` function. Add new function:
```typescript
 testPrint(): void {
        const printVar = new Print();
        printVar.print("test print");
    }
```
* Set cursor to `printVar.print`. And invoke Assistant -> Find Definition. Check opening the `printTest.ts` file. The `print` function should be selected.
* Repeat previous step using F4 key instead of Assistant -> Find Definition invocation
5. **Clang language server:**
* Create a workspace through Dashboard based on Default C++ language server. Create the _**console-cpp-project**_ from the wizard. 
* Open hello.cc file and make sure that  language server has been initialized. Go to the _**dev-machine**_ tab  and check that message like`2018-04-24 14:37:56,579[rverInitializer]  [INFO ] [.a.l.LanguageServerInitializer 109]  - Started language servers initialization, file path '/cpp/hello.cc'` is present.
Set cursor to the 7 line. Delete the line. Type `std::`. Make sure that error marker with `expected unqualified-id` message appears. 
* Type `std::cou` and launch code assistant by Ctrl+Space. Select `cout Outstream` from the proposal menu. Type `<< "Hello World!;"` Make sure that there is no any errors. 
* Erase `std::``. Make sure that error marker appears in line 7. Add `using namespace std;`in the line 4. Make sure that there is no any errors.
* Add new file for example: `iseven.h` and add content: 
```cpp
#ifndef VARIABLE
#define VARIABLE

int isEven(int arg);

#endif
```
* Create the new cpp file: `iseven.cpp` and add next:
```cpp
int isEven(int x) {
    return x % 2 == 0;
}
```
* Close all opened files except`hello.cc`. Set next content: 
```cpp
#include <iostream>
#include "iseven.h"

void test(int);

int main()
{
  int x = 4;
  std::cout << "Hello World!" << std::endl;
  std::cout << isEven(x) << std::endl;
  return 0;
}
```
* Set cursor to `isEven` and invoke Assistant -> Find Definition. Check opening the `iseven.h` file. The `int isEven(int arg);` function should be selected.

6. **Yaml language server:**
* Create a workspace through Dashboard based on Java. Go to the workspace. Profile -> Prefernces. Set the YAMPL schema: Select `Yaml`->Add Schema URl button -> type kubernetes.
* Create the **blank** project from the wizard. 
* Create for example openshift.yaml project file. Make sure that language server has been initialized. Go to the _**dev-machine**_ console and check message like: `[INFO ] [.a.l.LanguageServerInitializer 109]  - Started language servers initialization, file path '/yaml/openshift.yaml'`
* Type `k` and launch authocomplete (Ctrl+Space). Make sure that kind value is present in the proposal widget, check document window with content: `Kind is a string value representing the REST resource this object represents. Servers may infer this from the endpoint the client submits requests to. Cannot be updated. In CamelCase. More info: http://releases.k8s.io/HEAD/docs/devel/api-conventions.md#types-kinds`. Enter this value.
*Type: and launch authocomplete, select `PersistentVolume`. Make sure that there is no errors.
* Go to the new line type api, launch authocomplete,make sure that `apiVersion` has been pased. Type `: `launch authocomplete, `v1` value should be added.
* Go to the new line type `me`. Launch authocomplete. `metadata` should be pasted. Type `: `.  Launch authocomplete.
* Go to the beginning string and add some tabs. The error marker should appear. Remove the tabs. The YAML should be valid again
7. **Camel language server:**
* Create a workspace through Dashboard based on Default Java stack. Enable `Apache Camel` language server by slider on dashboard if needed.
Go to the just created workspace. Make sure that language server has been initialized. Go to the _**dev-machine**_ console and check message like: `Initialized Language Server org.eclipse.che.plugin.camel.server.languageserver on project file:/...` Create for example empty project and add the file: `camel.xml`. Add content into the file like this:
```xml
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
      <from uri="cxf:bean:reportIncident"/>
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
* Go to the `<from uri="cxf:bean:reportIncident"/>` section of `the apache.xml file`. Change `<from uri="cxf:bean:reportIncident"/>`to` <from uri="tim"/>` and invoke `ctrl + Space`. Select `timer:timerName` from the proposal menu.  Check document docker window.  Make sure that content like:`The timer component is used for generating message exchanges when a timer fires.` is present. Paste the selected  content (`timer:timerName`) from codeassist. Type `?`. Invoke codeassistant again by `ctrl + Space`. Make sure that `fixedRate=false` fragment has been pasted properly. Type `&amp;`. Invoke codeassistant, select `exchangePattern`into proposal menu. Invoke ctrl + Space again. Paste `InOnly` param.

