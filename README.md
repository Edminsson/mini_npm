# Npm package experiments
I've created this repository to experiment with npm packages. 
I want to create, publish and update npm packages. 
I also want to make git tags and use the script property "prepublish" in package.json to call grunt tasks.
I want to be able to only publish distribution files and not source files.

I want to understand what's being copied to the "npm modules" folder when someone calls "npm install <my package>".

##Creating an npm package
- Follow these instructions to create an npm package https://docs.npmjs.com/getting-started/creating-node-modules
- To use grunt, grunt-contrib-jshint and grunt-contrib-concat I first installed the packages using:
npm install &lt;package&gt; --save
- Configured Gruntfile.js following the instructions in http://gruntjs.com/sample-gruntfile
- I started with some simple tasks. Running jshint and concatenating files to the dist folder creating a 
main js file that has the same name as the name property in the package.json file.
- I added a main property to package.json as "dist/axelsPakettest.js". This file is what's loaded when the 
npm package is loaded when the module is required.

##Publishing the package
- Create or login as an npm user. You can either register a user or login as an existing user using the
command npm adduser. You may have problems login in if your npm version is too old. It happened to me.
- Publishing your package is as easy as calling the command: npm publish.
- I used this site https://docs.npmjs.com/getting-started/publishing-npm-packages