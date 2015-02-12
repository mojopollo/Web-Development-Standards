# Web Development Standards

Environment setup, notes, guidelines and standards.

***

## Sublime Text 3 - Install
* Download latests at http://www.sublimetext.com/3
* Install package control from: https://packagecontrol.io/installation

***

## Sublime Text 3 - Installing packages
For any packages that need to be installed you will do the following shortcuts:

Note: "Cmd" for Mac's, "Ctrl" for everything else

* Cmd/Ctrl + Shift + P
* Install Package + Enter
* **<package name>** + Enter

***

## JavaScript - Setup linter (JSLint)
* Install sublime package: **JSLint**
* Go to: Sublime -> Preferences -> Package Settings -> JSLint -> "Settings - Default"
* Then go to: Sublime -> Preferences -> Package Settings -> JSLint -> "Settings - User"
* Copy all contents from "Settings - Default" tab to "Settings - User" tab and Save
* In "Settings - User" replace the "options" array with the following and Save:
```json
// an array of options to pass to jslint.
"options" : [

    // examples using predef flag.
    "--predef", "['angular', 'document', '\\$', '_', 'JQuery', 'FB']"
    // tolerate missing 'use strict' pragma.
    // ,"--sloppy"
    // suggest an indent level of two spaces.
    ,"--indent", "2"
    // assume node.js to predefine node globals.
    ,"--node"
    // tolerate unfiltered for in.
    //,"--forin"
    // tolerate dangling _ in identifiers.
    // ,"--nomen"
    // tolerate many var statements per function.
    // ,"--vars"
    // tolerate ++ and --.
    // ,"--plusplus"
    // tolerate blocking -Sync methods
    // ,"--stupid"
    // tolerate comments starting with TODO
    // ,"--todo"

]
```
* From now on, all javascript files on Save, will run through JSLint and output errors until you follow the strict guidelines
* Get familiar with common errors and guidelines here: http://www.jslint.com/lint.html
* Get help on fixing the errors here: http://jslinterrors.com/
* The goal is to have "0 errors" on Save

***

## CoffeeScript - Setup linter (Part 1 of 3 : Better CoffeeScript)
* Install Node :
```bash
$ brew install node
```
* Install CoffeeScript :
```bash
$ npm install -g coffee-script
```
* Install sublime package: **Better CoffeeScript**
* Go to: Sublime -> Preferences -> Package Settings -> Better CoffeeScript -> "Settings - User"
* In "Settings - User" , set the following :
```json
{
    "binDir": "coffeescript-install-directory"
}
```
set coffeescript-install-directory to the install directory of the **coffee** command, for example the command :
```bash
$ which coffee
```
returns
```bash
/usr/local/bin/coffee
```
the CoffeeScript install directory is ```/usr/local/bin/``` (without the word "coffee")

* Note: ```Alt + Shift + D``` will preview the compiled CoffeeScript code

***

## CoffeeScript - Setup linter (Part 2 of 3 : SublimeLinter)
* Install sublime package: **SublimeLinter**

***

## CoffeeScript - Setup linter (Part 3 of 3 : SublimeLinter-coffee)
* Install sublime package: **SublimeLinter-coffee**
* Go to: Sublime -> Preferences -> Package Settings -> SublimeLinter -> "Settings - User"

***

