# Web Development Standards

Environment setup, notes, guidelines and standards.

***

## Local Package Manager - (Mac)
* Follow instructions and install http://brew.sh/

***

## Install required binaries - (Mac)
* ```brew install bash-completion```
* ```brew install imagemagick```
* ```brew install ghostscript```
* ```brew install mcrypt```
* ```brew install node```
* ```brew install php55```
* ```brew install php55-mcrypt```
* ```brew install s3cmd```
* ```brew install ssh-copy-id```
* ```brew install wget```

***

## Third Party Development Applications - (Mac)
* https://iterm2.com/downloads.html
* Spolight http://www.alfredapp.com/#download
* MySQL Database Management for Mac OS X - http://www.sequelpro.com/

***

## Setting Up Bash Environment - (Mac)
* modify or create your bash profile via the terminal: ```nano ~/.bash_profile```
```bash
# Start - Git branch on bash prompt
function parseGitBranch {
        git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ \[\1\]/'
}

function setBashPrompt {

        local        BLUE="\[\033[0;34m\]"

        # OPTIONAL - if you want to use any of these other colors:
        local RED="\[\033[0;31m\]"
        local LIGHT_RED="\[\033[1;31m\]"
        local GREEN="\[\033[0;32m\]"
        local LIGHT_GREEN="\[\033[1;32m\]"
        local WHITE="\[\033[1;37m\]"
        local LIGHT_GRAY="\[\033[0;37m\]"
        # END OPTIONAL

        local     DEFAULT="\[\033[0m\]"

        # old git prompt
        #PS1="\h:\W \u$BLUE\$(parseGitBranch) $DEFAULT\$"

        # new path prompt
        export PS1="\u@\h \w$LIGHT_GREEN\$(parseGitBranch) $DEFAULT$ "
}

setBashPrompt
# End - Git branch on bash prompt

export CLICOLOR=1
export LSCOLORS=gxBxhxDxfxhxhxhxhxcxcx

alias ll="ls -lah"

# Put color in these commands
alias composer='composer --ansi'
alias grep='grep --color'

# brew bash completion
if [ -f $(brew --prefix)/etc/bash_completion ]; then
  . $(brew --prefix)/etc/bash_completion
fi
```

* Now your path inside a Git repo in terminal will more like this:
```bash
mojo@m ~/www/shindiig/website/repo [devel] $
```

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
the CoffeeScript install directory is ```/usr/local/bin/``` (without the word "coffee"), so the config looks like:
```json
{
    "binDir": "/usr/local/bin/"
}
```

* Note: ```Alt + Shift + D``` will preview the compiled CoffeeScript code
* Note: this package adds syntax highlight ```Better CoffeeScrip -> CoffeeScript``` which is the syntax you must have lighting for the linter in Part 3 t work

***

## CoffeeScript - Setup linter (Part 2 of 3 : SublimeLinter)
* Install sublime package: **SublimeLinter**

***

## CoffeeScript - Setup linter (Part 3 of 3 : SublimeLinter-coffee)
* Install sublime package: **SublimeLinter-coffee**
* Go to: Sublime -> Preferences -> Package Settings -> SublimeLinter -> "Settings - User"
* make sure the following paths are set to your ```coffee``` binary and ```node``` binary
```json
    "coffee_path": "/usr/local/lib/node_modules/coffee-script/bin",
    "node_path": "/usr/local/bin",
```
* Note: For this linter to work you must have syntax highlighting set to ```Better CoffeeScript -> CoffeeScript``` in order for the coffee linter to work

***

## CoffeeScript - Autocomplete triggers
* Go to: Sublime -> Preferences -> "Settings - User"
* adding the following will enable autocomplete
```json
{
    "auto_complete_triggers":
    [
        {
            "characters": ".@",
            "selector": "source.coffee, source.litcoffee, source.coffee.md"
        }
    ]
}
```
* Note: you can add other syntax like ```*.php``` would be ```source.php``` and the auto complete behavior woud be the same for php syntax files

***

## Sublime Text 3 - Indentation & white-space trimming
* Go to: Sublime -> Preferences -> "Settings - User"
```json
{
    "tab_size": 2,
    "translate_tabs_to_spaces": true,
    "trim_trailing_white_space_on_save": true,
    "ensure_newline_at_eof_on_save": true
}
```
* Quit and reopen Sublime Text 3

***

## Sublime Text 3 - Optional helpful preferences
* Go to: Sublime -> Preferences -> "Settings - User"
```json
{
    "highlight_line": true,
    "line_numbers": true,
    "scroll_past_end": true,
    "show_full_path": true,
    "highlight_modified_tabs": true,
    "enable_tab_scrolling": false,
    "bold_folder_labels": true
}
```
* Quit and reopen Sublime Text 3

***

## Git Branching Methodology

* http://nvie.com/posts/a-successful-git-branching-model/

![Git Branching Methodology](http://nvie.com/img/git-model@2x.png)

***
