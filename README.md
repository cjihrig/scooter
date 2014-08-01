<a href="https://github.com/spumko"><img src="https://raw.github.com/spumko/spumko/master/images/from.png" align="right" /></a>
![scooter Logo](https://raw.github.com/spumko/scooter/master/images/scooter.png)

**Scooter** is a User-agent information plugin for [**hapi**](https://github.com/spumko/hapi)

[![Build Status](https://secure.travis-ci.org/spumko/scooter.png)](http://travis-ci.org/spumko/scooter)

Lead Maintainer: [Daniel Bretoi](https://github.com/danielb2)


Scooter uses the [useragent] package to provide user-agent information. For
more details of what information scooter provides, please see the useragent web-page.

[useragent]: https://www.npmjs.org/package/useragent

# Usage

``` javascript
    var Hapi = require('hapi');
    var server = new Hapi.Server(8086);
    var Scooter = require('../');

    server.route({
        method: 'GET',
        path: '/user-agent',
        handler: function (request, reply) {

            return reply(request.plugins.scooter.toJSON());
        }
    });

    server.pack.register({ plugin: Scooter }, function(err) {
        server.start(function () {
            console.log(server.info.uri + '/user-agent');
        });
    });
```
