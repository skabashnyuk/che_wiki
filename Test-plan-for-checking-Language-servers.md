Unfortunately we do not have any functional test specification for covering language servers. For testing we had only simple test cases for covering base functionality based on positive testing. 
The language servers was checked next way:
1. **PHP language server:**
* Create a workspace through Dashboard based on Default PHP stack. Enable php language server. by slider on dashboard if it need.
* Go to the just created workspace and create **_web-php-simple_** project with wizard
* Open **_index-php_** file and make sure that language server has been initialized. Go to the _**dev-machine**_ console and check message like: `2018-04-23 08:47:03,059[rverInitializer]  [INFO ] [.a.l.LanguageServerInitializer 216]  - Initialized language server 'org.eclipse.che.plugin.php.languageserver'`
* Add an error in the `echo` command and check that error marker is appeared. Click on error marker - the proposal widget should be present. Restore content. Error marker should disappear.
* Add variable like `$color = "blue";`. Make sure that there is no errors. Go to the end of `echo "Hello World!"` type `$` and launch autocompletion by Ctrl+Space. The `color` fragment should be completed.
* Set cursor to the new line type `e` and launch autocompletion by Ctrl+Space. Check that proposal is present, see link below:
[PHP autocoplete proposal](https://www.dropbox.com/s/2hrzg04hqbz1a4j/Selection_012.png?dl=0)

2. **Python language server:**
* Create a workspace through Dashboard based on Default python stack. Enable language server by slider on dashboard  if it need.
* Go to the just created workspace and create _**console-python3.5-simple**_. Open the `main.py`file. and make sure that language server has been initialized. Go to the _**dev-machine**_ console and check message like: `and make sure that language server has been initialized. Go to the _**dev-machine**_ console and check message like: ...`
* Add an error in the `print` command and check that error marker is appeared. Click on error marker - the proposal widget should be show `invalid syntax` message. Restore content. Error marker should disappear.
type. Remove content from the file and paste code like:
`class MyClass:
    var = 1
    variable = "bla"

    def function(self):
        print("This is a message inside the class.")`
Add empty line. Make sure that warning marker with message: `W293 blank line contains whitespace` is present
* Add empty line again and type code fragment like `myobjectx = MyClass()`
* Press enter and type myobjectx, than ctrl+space. Make sure that `function`, `var` and `variable` fields are available from the class in the proposal menu.

3. **JSON language server:**
*Create a workspace through Dashboard based on Default Node Stack. Enable JSON language server by slider on dashboard  if it need.
* Go to the just created workspace and create _**nodejs-hello-world*_. Open the `package.json`file. and make sure that language server has been initialized. Go to the _**dev-machine**_ console and check message like: `2018-04-23 13:00:27,948[rverInitializer]  [INFO ] [.a.l.LanguageServerInitializer 109]  - Started language servers initialization, file path '/nodeJs/package.json'`
* Remove `,` symbol after `}`. Make sure that error marker appears. Click on the marker and check message like `Expected '(end)' and instead saw ':'.`in the proposal window. Return the just deleted coma and wait disappearance the marker. Go to the line 9 and add fragment like: `"newObj":[1,2,3],`. Make sure that JSON does not have any errors.

4. **Type script language server:**
* Create a workspace through Dashboard based on Default Node Stack. Enable TypeScript language server by slider on dashboard  if it need.
* Go to the just created workspace and create _**nodejs-hello-world*_. Open the `package.json`file. and make sure that language server has been initialized. Go to the _**dev-machine**_ console and check message like: `[INFO ] [.a.l.LanguageServerInitializer 216]  - Initialized language server 'org.eclipse.che.plugin.web.typescript`.
Add new file like: `Greeter.ts` wit next content: 
`class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
}

let greeter = new Greeter("world");`
* Add space into keyword class-> c lass. Make sure that error markets have appear. Click on first marker and check the message like: `cannot find lass`
* Remove the space - error makers should disappear. Add empty line after the code and type `greeter.`. Sent ctrl+space. Make sure that `freet()` function and `greeting` field are present in the proposal panel.

5. **Clang language server:**
*Create a workspace through Dashboard based on Default C++ language server

