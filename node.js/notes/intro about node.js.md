- it is basically a java script runtime environment where js code can run with extra tools like (like access to files, networks and server) that browser didn't give you.
- it is like a special program that let js run outside the browser, mainly on your computer or a server.
# how browser is different from node.js

| browser                                                                                                                                         | node.js                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| dom                                                                                                                                             | no dom                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| window                                                                                                                                          | no window                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| interactive apps                                                                                                                                | server side apps                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| no file system                                                                                                                                  | file system                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| fragmentation due to different browsers and their different versions                                                                            | fragmentation is due to different versions of the node.js only.                                                                                                                                                                                                                                                                                                                                                                                     |
| global object is window, any variable declare with var keyword outside the function became the global variable or property of the global object | global object is global, any variable declared with var, let, const didn't became the global object, because in node each file is treated as its own module with its own scope, not shared global scope like in browsers. <br>to make the variable global in node we have to do <br>global.name = 'anmol';<br>console.log(global.name);<br>note - global variables in node are those variables that we can access them anywhere in the application. |
| use import at the top level                                                                                                                     | use require() anywhere in the code                                                                                                                                                                                                                                                                                                                                                                                                                  |

# how to create and run first node app
- create a folder and i vs code create a file let say app.js
- then open cmd and locate it to the folder
- then write node app.js
- and boom the code that you have written in the file runs here.
- note - you can do the same thing in terminal in vs code also. and the good part is that it already points to the same folder.
- example give below (app.js)
```
const amount = 1;

if(amount < 10) {
  console.log('small');
}
else {
  console.log('large');
}
console.log(`hey this is my first node app`);
```
# CommonJS modules
- every file is a module in CommonJS modules
- used module.exports and require for exporting and importing
- doesn't need to write require at the top of the file you can write it anywhere in the code.
- module itself is a object and exports is the another object inside module so to access the exports we have to do like this module.exports and now we can add any functions or properties in that object and call require() in any other file in which we want to import those functions and properties.
## Info about modules path

| type             | path start with                                                    |
| ---------------- | ------------------------------------------------------------------ |
| local            | starts with ./ or ../                                              |
| absolute         | startw with /(unix and linux) or C:\(windows)                      |
| built in modules | starts with nothing (no need to install)<br>example require('os'); |
| external modules | starts with nothing (need to install)                              |
