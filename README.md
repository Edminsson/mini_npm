# Npm package experiments
I've created this repository to experiment with npm packages. 
I want to create, publish and update npm packages. 
I also want to make git tags and use the script property "prepublish" in package.json to call grunt tasks.
I want to be able to only publish distribution files and not source files.

I want to understand what's being copied to the "npm modules" folder when someone calls "npm install <my package>".
The package that I finally created publishes a dist folder. This folder is not in the repository but gets created
when the package is published using the prepublish property in package.json.

##Creating an npm package
- Follow these instructions to create an npm package https://docs.npmjs.com/getting-started/creating-node-modules
- To use grunt, grunt-contrib-jshint and grunt-contrib-concat I first installed the packages using:
npm install &lt;package&gt; --
- I created a .ignore file so that node_modules and bower_components do not get copied to github.
- Configured Gruntfile.js following the instructions in http://gruntjs.com/sample-gruntfile
- I started with some simple tasks. Running jshint and concatenating files to the dist folder creating a 
main js file that has the same name as the name property in the package.json file.
- I added a main property to package.json as "dist/axelsPakettest.js". This file is what's loaded when the 
npm package is loaded when the module is required.

##Publishing the package axelsnpmpaket
- Create or login as an npm user. You can either register a user or login as an existing user using the
command npm adduser. You may have problems login in if your npm version is too old. It happened to me.
- Publishing your package is as easy as calling the command: npm publish.
- I used this site https://docs.npmjs.com/getting-started/publishing-npm-packages
- I discovered that if I use dependencies instead of devDependencies in package.json the dependencies
 get installed along with the package at installation.
- I'm also using the files-properties in package.json to only install the dist-folder when the package gets installed.
- To make a new version of the package you can edit the package.json manually or you can use "npm version patch",
"npm version minor", "npm version major" depending of what kind of update you are doing. Using the "npm version" command
in a git repository you automatically make a tag. You will have to push the tag manually to github.
- After making a new version you have to call "npm publish" again. 

## Installing the package
- When I use "npm install axelsnpmpaket" only the dist folder, package.json and the readme file gets copied.
- If I use "npm install edminsson/mini_npm" only package.json and the readme file gets copied. That's because of
the files property and the fact that the the dist folder is not in the repository. I tried to add an extra folder to both the files property
in package.json and to the repository and this new folder gets copied when installing the package directly from
github without using the published package.
- The main file in the package also contains a printMsg in the exportsobjekt so it can be used when the package
is required. I.e. demo = require('axelsnpmpaket'); demo.printMsg();  

##Commands
- npm adduser or npm login
- npm publish
- npm version patch (updates the last digit in the version 1.0.1 to 1.0.2. If it's a git repo it creates a tag and commits it)
- After "npm version patch" you must do a new "npm publish"