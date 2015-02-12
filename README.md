## Web Development Standards

Environment setup, notes, guidelines and standards.

### Sublime Text 3 - Install
* Download latests at http://www.sublimetext.com/3
* Install package control
from: https://packagecontrol.io/installation
```bash
import urllib.request,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

### Javascript - Setup linter
* Install sublime package: JSLint
* Go to: Sublime -> Preferences -> Package Settings -> JSLint -> "Settings - Default"
* Then go to: Sublime -> Preferences -> Package Settings -> JSLint -> "Settings - User"
* Copy all contents from "Settings - Default" tab to "Settings - User" tab and Save
* Replace the "options" array with the following and Save:
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
* From now on, all javascript files on Save, will run through JSLint, get familiar with common errors and guidelines here: http://www.jslint.com/lint.html