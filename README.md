Express-CSRF: Cross-site request forgery protection for Express Node.js framework
=================================================================================

`express-csrf` is a simple helper for enabling cross-site request forgery protection in Express applications.

It provides a csrf token to views using dynamicHelpers, which is also saved in the session. With a middleware check, the csrf token in the request body is checked against the one in the session, to make sure that they match.

## Version
0.2.0

## Requirements
- [Node](http://github.com/ry/node)
- [Express](http://github.com/visionmedia/express)

## Installation

Recommended installation is with git submodules. To add express-csrf to your project, do:

    git submodule add http://github.com/hanssonlarsson/express-csrf.git lib/support/express-csrf

You can also install express-csrf with npm:

    npm install express-csrf

## Usage

    var express = require('express'),
        csrf = require(__dirname + '/lib/support/express-csrf');
    
    app = express.createServer();
    
    app.dynamicHelpers({
        csrf: csrf.token
    });
    
    app.use(express.session());
    app.use(express.bodyDecoder());
    app.use(csrf.check());
    
    app.listen(3000);

In your view:

    <form>
        <input type="hidden" name="csrf" value=csrf>
    </form>

## Credits

Linus G Thiel &lt;linus@hanssonlarsson.se&gt;

## Thank you

- [Ryan Dahl](http://github.com/ry) for the awesome Node.js
- [Visionmedia](http://github.com/visionmedia) for Express
- [Tane Piper](http://github.com/tanepiper) for letting us know about Node's crypto module

## License 

(The MIT License)

Copyright (c) 2010 Hansson &amp; Larsson &lt;info@hanssonlarsson.se&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
