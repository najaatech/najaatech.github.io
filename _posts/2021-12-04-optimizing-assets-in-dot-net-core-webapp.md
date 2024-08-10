---
layout: post
title: "Optimizing assets in .NET Core WebApp"
date: 2020-12-04 20:00:00 +0300
categories: technology development dotnet core
author: Anas Najaa
---

![Optimizing assets in .NET Core WebApp](https://najaa-files.s3.me-south-1.amazonaws.com/blog/2024/08/916265dc-958d-4671-a433-11e55a5ad377.png)

When serving website's static assets, it is alway recommended to reduce the number and the size of requests made on each page. In .NET Core, there are two useful libraries that work very well in Web App projects. In this article, we are going to describe how to use Build Minifier to reduce the number and size of our static assets. In addition, we will use Web Compiler to streamline the process of writing and minifying our CSS files using SCSS.

> Disclaimer: BuildWebCompiler is not actually cross platform while BuildBundlerMinifier is. Please keep this in mind if you are planing to use it in your project.

# About the packages

-   [BuildWebCompiler](https://github.com/madskristensen/WebCompiler) : Used to compile and minify .less and .scss files
-   [BuildBundleMinifier](https://github.com/madskristensen/BundlerMinifier) : Used to bundle multiple CSS, JS or HTML files into a single file

# Base Project

We are going to start from a Web Application template project. Go to Visual Studio, create a new project and select Web Application starter template. You can go through the setup wizard normally as most of the configurations are not related to the nature of our task.

# Downloading the packages

In Visual Studio, we need to go to tools > Nuget Package Manager > Package Manager Console. Type in the following commands to install both packages:

-   `Install-Package BuildBundlerMinifier -Version 3.2.449`
-   `Install-Package BuildWebCompiler -Version 1.12.405`

# WebCompiler

First, let's create a file under the name "style.scss" in the path wwwroot\css. In order to create this file, you can right click the css folder > select add class and then type style.scss. After the file is created, make sure to clear the content of the file as the added code is for the class template file not the scss file. After clearing the content, we will add some sample code to test if the compilation is done correctly or not:

**wwwroot\css\res\style.scss**

```scss
$bg-color: #f5f5f5;

body {
	background: $bg-color;
}
```

Now if we try to build the solution, it will build successfully but no .css or .min.css files will be generated. We need to create a configuration file that will tell the WebBildCompiler the input and output files. To do so, we need to right click the style.scss file then select > Web Compiler > Compile File. This will create compilerconfig.json file with the following configurations:

**compilerconfig.json**

```json
[
	{
		"outputFile": "wwwroot/css/style.css",
		"inputFile": "wwwroot/css/style.scss"
	}
]
```

We will see that two new files were created, style.css and style.min.css. With that, we achieved the first step of our optimization task. This build process will happen each time we change the content of the file and save the changes. You can test it out by changing the color of the variable bg-color.

# BuildBundleMinifier

Next, let us include some JS files into our project. These files can contain anything really, but usually we want to minify and bundle any third party library. This way we serve a single minified JS file that contains everything we are using in our project. Let's start by creating two files called lib1.js and lib2.js inside wwwroot\js. We can use the same trick as before, right click the js folder > add class > lib1/lib2.js. Make sure to clear the content afterwards. In addition to the JS files, we want to include lib1.css and lib2.css inside the path we created earlier wwwroot\css. What we are trying to simulate is the addition of third party libraries. Usually, third party libraries require .js and .css files to work properly. Now that we created all of our four files, we need to start adding test content to them:

**wwwroot\js\lib1.js**

```javascript
function addTwoNumbers(num1, num2) {
	return num1 + num2;
}
```

**wwwroot\js\lib2.js**

```javascript
function postRequest(url, data) {
	const headers = new Headers();
	headers.append("Content-Type", "application/json");
	const raw = JSON.stringify(data);
	const options = {
		method: "POST",
		headers: headers,
		body: raw,
		credentials: "include",
	};
	return fetch(url, options).catch((error) => console.log(error));
}
```

**wwwroot\css\lib1.css**

```css
.test {
	color: red;
	margin-left: 1.2rem;
	padding-top: 120px;
}
.test2 {
	font-size: 1.7rem;
	font-weight: 300;
	color: blue;
}
```

**wwwroot\css\lib2.css**

```css
.test3 {
	color: gray;
	margin-top: 0;
	margin-bottom: 16px;
}
.test4 {
	font-size: 50px;
	line-height: 1.5;
	color: orange;
}
```

Afterwards, we need to create a configuration file that will tell the minifier to target which files and to output them under what name. Similar to the configuration file we created earlier, we create bundleconfig.json in the root directory:

**bundleconfig.json**

```json
[
	{
		"outputFileName": "wwwroot/css/lib.min.css",
		"inputFiles": ["wwwroot/css/lib1.css", "wwwroot/css/lib2.css"]
	},
	{
		"outputFileName": "wwwroot/js/lib.min.js",
		"inputFiles": ["wwwroot/js/lib1.js", "wwwroot/js/lib2.js"],
		"minify": {
			"enabled": true,
			"renameLocals": false
		},
		"sourceMap": false
	}
]
```

Now all we need to do is build the project by pressing F6. This will create lib.min.css and lib.min.js files in the directories we specified in the configuration file.

With that, we created a simple, yet effective setup that will help us in publishing a smaller more compact static files to our hosting. Now all that remains is to do some small tweaks to improve the development experience when we are working locally.
