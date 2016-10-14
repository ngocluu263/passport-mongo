passport-mongo
==============

This repository serves as an example of a basic Node.js application which is using [Passport](http://passportjs.org/) as the authentication middleware for authenticating against a locally configured Mongo backend

Steps to run the app
=====================
* After cloning the repo, install the dependencies by running **npm install**
* To start the server, run **npm start** on the base directory

Perquisites
============
The server assumes that you have a local mongo instance running. This means if you have mongo installed locally, all you need to do is configure the db.js file correctly and run the mongod daemon

fix error:

{ Error: Cannot find module '../build/Release/bson'
    at Function.Module._resolveFilename (module.js:455:15)
    at Function.Module._load (module.js:403:25)
    at Module.require (module.js:483:17)
    at require (internal/module.js:20:19)
    at Object.<anonymous> (/opt/passport-mongo/node_modules/bson/ext/index.js:15:10)
    at Module._compile (module.js:556:32)
    at Object.Module._extensions..js (module.js:565:10)
    at Module.load (module.js:473:32)
    at tryModuleLoad (module.js:432:12)
    at Function.Module._load (module.js:424:3) code: 'MODULE_NOT_FOUND' }
js-bson: Failed to load c++ bson extension, using pure JS version


=>
find in npm module mongodb ..node_modules\mongodb\node_modules\bson\ext\index.js

and change path to js version in catch block

bson = require('../build/Release/bson');

to

bson = require('../browser_build/bson');

or copy file in

    ..node_modules\bson\build\Release\bson

from

    ..node_modules\bson\browser_build\bson

