# butter_remote.js
butter_remote.js is a javascript library that provides an easy way to make an application or whatever you want to control the interface of [butter](http://butterproject.org/) through the json rpc protocol.<br>
The plugin is developed with simplicity in mind so the methods name are the same that you can find in the [butter documention](https://github.com/butterproject/butter-desktop/blob/master/docs/API/json-rpc-api.md) and there are many other conveniences. So despite that doc has been written with the json rpc protocol in mind, the information about the usage of the methods are compatible for this library too... actually you will not even notice that you're using this library.

## Download
You can get the plugin in two ways:

1. Downloading the raw file in the dist folder choosing the [clean](https://raw.githubusercontent.com/giacomocerquone/butter_poremote.js/master/dist/butter_remote.js) or [minified](https://raw.githubusercontent.com/giacomocerquone/butter_remote.js/master/dist/butter_remote.min.js) version.
2. Go to the releases tab and download the [Source code.zip]()

## The website
Actually the website that you can find on the [gh-pages branch](https://github.com/giacomocerquone/butter_remote.js/tree/gh-pages) hosted on [butter.giacomocerquone.com](http://butter.giacomocerquone.com) is the coolest thing in here. It's just a draft to prove the potential of this library and what you can do with it. I'll do my best to improve it but I haven't so much free time so if you want to contribute I would really appreciate that!

## Include and Initialize
Firstly you should obviously include the library on the page you want to use it:
```html
<script src="butter_remote.min.js"></script>
```
After initialize the plugin in this way:
```javascript
butter_remote.init(
//If you don't need to change these settings you can remove this whole part
  {
    username: "popcorn",
    password: "popcorn",
    ip: "127.0.0.1",
    port: "8008",
    debug: "false"
  }
//If you don't need to change these settings you can remove this whole part
);
```

## Usage
As you can understand from the butter time documentation, there are "three kinds" of methods.

##### Methods which performs actions without any parameter needed.<br>
These are {listing methods}:<br>
```javascript
butter_remote.ping();
```
##### Methods that need parameters to performs certain actions.<br>
These are {listing methods}:<br>
```javascript
butter_remote.filtergenre(["Adventure"]);
```
##### Methods which performs actions and return some data.<br>
Here you have a callback function and the data can be accessed in this way:
```javascript
//This get the current volume in the player
butter_remote.volume(function(data) {
  console.log(data);
});
//This set the current volume in the player
butter_remote.volume([2]);
```

##### The listennotification function
I'd like to spend two words for this particular function. butter developers put this fundamental function in their API to know when something change on the desktop application. To listen these important events you need to use "setInterval" so you can call the function at specified intervals, here the example:
```javascript
setInterval(function() {
    pr.listennotifications(function(data) {
        //Use the data object to read the notifications
        //and do wathever you need with the notifications you just took (changing commands etc.)
    })
}, 1000);
```

## License
Released under the GNU 3 license.<br>
If you distribute a copy or make a fork of the project, you have to credit this project as source.<br>
Copyright © 2015, Giacomo cerquone.<br>
All rights reserved.
