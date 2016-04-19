# Frontend Automate Skeleton
Extract from [Sage](https://travis-ci.org/roots/sage)
Modified by DuyDuc-Nguyen

## Requirements

| Prerequisite    | How to check | How to install
| --------------- | ------------ | ------------- |
| Node.js 0.12.x  | `node -v`    | [nodejs.org](http://nodejs.org/) |
| gulp >= 3.8.10  | `gulp -v`    | `npm install -g gulp` |
| Bower >= 1.3.12 | `bower -v`   | `npm install -g bower` |

## Features

* [gulp](http://gulpjs.com/) build script that compiles both Sass and Less, checks for JavaScript errors, optimizes images, and concatenates and minifies files
* [BrowserSync](http://www.browsersync.io/) for keeping multiple browsers and devices synchronized while testing, along with injecting updated CSS and JS into your browser while you're developing
* [Bower](http://bower.io/) for front-end package management
* [asset-builder](https://github.com/austinpray/asset-builder) for the JSON file based asset pipeline
* [Bootstrap](http://getbootstrap.com/)
* [Sass Mixins Helpers](#sass-mixins) to create media queries.

## Install

From the command line, you'll want to do this inside the folder where you want your project to be on your computer

`git clone https://github.com/duyduc-nguyen/frontend-workflow-skeleton.git my-project` 

Building the theme requires [node.js](http://nodejs.org/download/). We recommend you update to the latest version of npm: `npm install -g npm@latest`.

From the command line:

1. Install [gulp](http://gulpjs.com) and [Bower](http://bower.io/) globally with `npm install -g gulp bower`
2. Navigate to your project folder, then run `npm install`
3. Run `bower install`

You now have all the necessary dependencies to run the build process.

### Setting your path

You can change the paths of source and dist folders via `assets/manifest.json`. For example:

```json
...
  	"paths": {
		"source": "resources/assets/",
    	"dist": "public/dist/"
  	}
...
```

For more information about `manifest.json`, you can visit [asset-builder](https://github.com/austinpray/asset-builder).

### Available gulp commands

* `gulp` — Compile and optimize the files in your assets directory
* `gulp watch` — Compile assets when file changes are made
* `gulp --production` — Compile assets for production (no source maps).

### Using BrowserSync

To use BrowserSync during `gulp watch` you need to update `devUrl` at the bottom of `assets/manifest.json` to reflect your local development hostname.

For example, if your local development URL is `http://project-name.dev` you would update the file to read:
```json
...
  "config": {
    "devUrl": "http://project-name.dev"
  }
...
```
If your local development URL looks like `http://localhost:8888/project-name/` you would update the file to read:
```json
...
  "config": {
    "devUrl": "http://localhost:8888/project-name/"
  }
...
```
##Sass Mixins Helpers

```SCSS
	$min: min-width;
	$max: max-width;
	@mixin at-query($constraint_, $viewport1_, $viewport2_:null) {
	  ...
	}
```

| Name            | Type         | Description
| --------------- | ------------ | ------------- |
| $constraint     | `String`     | Options: **min-width**, **max-width**, or **null** |
| $viewport1      | `String`     | If **$constraint** is set to **max-width**:<br>* **$viewport1** will be your media query's **max-width**<br>If **$constraint** is set to **min-width** or **null**:<br>* **$viewport1** will be your media query's **min-width** |
| $viewport2      | `String`     | If set, this becomes the media query's max-width
								  Default: **null** |

Example:

```SCSS
	@include at-query($max, $small) {
	  .foo {
	    font-size: 0.8em;
	  }
	}
```

Output:

```CSS
	@media screen and (max-width: 480px) {
	  .foo { font-size: 0.8em; }
	}
```
