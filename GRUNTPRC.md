## grunt (concat config)

WTH is Grunt? It's a task runner. A build system. It will make you dev life easier, because with grunt you can automate the process of doing a lot of repetitive task. 
It is like a setup or configuration in your project, you will just do it once instead of doing the tasks all over and over.

### Procedures

1. Install first all the necessary packages for grunt to run.
Make sure the nodeJS is installed (download it here -> https://nodejs.org/en/download/)
Once the nodeJS is installed, you can run the following commands:
* ``npm install -g grunt-cli`` // the grunt command line interface
* ``npm init`` // initialize the project, it will produce package.js on the root folder
* ``npm install -S grunt`` // save it as project dependency
_Note: It will take some time to finish the install process_

2. Create "Gruntfile.js" on root directory, and paste sample code to test if grunt is working.

__Gruntfile.js code:__

```
module.exports = function(grunt){
	
	// sample code for creating a task 
	grunt.registerTask("<task-name>", function(){
		// task process
		console.log("Hello");
	)};
	
	// sample code for combining a task
	grunt.registerTask("<task-name> / "default"", ["<task-name1>", "<task-name2>"]);
}
```

3. If everything is working you can now configure your build system. You can find a lot of plugins here: https://gruntjs.com/plugins
Modify the code based on what you need on your project. (This is concatenation and watching the js files using
"grunt-contrib-concat" and "grunt-contrib-watch".

__Gruntfile.js code:__

```
module.exports = function(grunt){
	
	// The initial config sample code
	
	grunt.initConfig({
		concat: {
			// for options
			option: {
				separator: ";",
			}
			
			js: {
				src: ["js/main.js" , "js/partial.js"],
				dest: "build/js/script.js",
			}
		},
		watch: {
			js: {
				files: ["js/**/*.js"],
				tasks: ["concat:js"],
				options: {
					spawn: false,
				},
			}
		},
	});
	
	grunt.registerTask("default", ["concat", "watch"]); // running both tasks
	
	// Packages runner. More on https://gruntjs.com/plugins
	
	grunt.loadNpmTasks("grunt-contrib-concat");
	grunt.loadNpmTasks("grunt-contrib-watch");
}
```

4. After configuring your tasks you can now run your coded commands and start the project with a SMUG SMILE! 

> Sample grunt configuration for concatenating and watching files. Video tutorial link below was all translated into text for my future reference 
* Video Tutorial : https://www.youtube.com/watch?v=TMKj0BxzVgw
* Plugins: https://gruntjs.com/plugins
