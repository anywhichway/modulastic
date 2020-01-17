# modulastic

Express middleware to expose select Node modules to browser.

# Configuration Object

{
	appDir: string, // root directory below which node_modules can be found, usually __dirname
	<browserRoot>: {
		<nameToExpose>: {
			packageName: string, // actual node package name, optional, defaults to <nameToExpose>, useful for @ prefixed packages
			pathName: string // subdirectory under the module to expose, usually "dist"
		}
	},
	... more <browserRoot> objects, rarely used
}

# Example

import {modulastic} from "modulastic";

const app = express(); // obviously need to import express first

app.use(modulastic(app,{
	modules: {
		quill: {pathName:"dist"},
		jsoneditor: {pathName:"dist"},
		"dialog-polyfill": {pathName:"dist"},
		"fontawesome": {packageName:"@fortawesome",pathName:"fontawesome-pro"}
	}, 
	appDir:__dirname
}));

# License: MIT
