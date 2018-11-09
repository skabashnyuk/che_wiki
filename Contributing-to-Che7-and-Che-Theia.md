## Debugging a Theia-plugin
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
TODO: use debug hosted mode