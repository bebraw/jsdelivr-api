# Public CDNs API

Root: `/v1/<cdn>/libraries`

Supports `jsdelivr`, `google`, `cdnjs`, `bootstrap` and `jquery`.

Only GET requests are allowed. No limits are set.

Get all hosted libraries in JSON format

```
http://api.jsdelivr.com/v1/jsdelivr/libraries
http://api.jsdelivr.com/v1/google/libraries
http://api.jsdelivr.com/v1/cdnjs/libraries
http://api.jsdelivr.com/v1/bootstrap/libraries
http://api.jsdelivr.com/v1/jquery/libraries
```


Get full information for a single library based on `name` parameter.

```
http://api.jsdelivr.com/v1/jsdelivr/libraries?name=jquery
http://api.jsdelivr.com/v1/jsdelivr/libraries/jquery - alias
```

Get full information for any library starting with `jq` that has lastversion ending with `0.1`. [minimatch](https://www.npmjs.org/package/minimatch) syntax is supported.

```
http://api.jsdelivr.com/v1/jsdelivr/libraries?name=jq*&lastversion=*.0.1
```

You can use any of the following parameters to search for libraries. A search will be performed for projects matching your input. You can use multiple parameters at the same time. If multiple projects match they all will be outputed.

* `name` - name of library. Example: jquery
* `zip` - zip name of project. Example: jquery.zip
* `mainfile` - mainfile parameter in info.ini. Example: jquery.min.js
* `lastversion`- lastversion of the project. Example: 2.0.3 (will match multiple projects)
* `versions` -  all hosted versions for selected project. (read only)
* `description` - description of the project
* `homepage`- webpage of project. Example: http://jquery.com/
* `github`- github page of project. Example: https://github.com/jquery/jquery
* `author` - the author of project. Example: jQuery Foundation
* `assets` - files hosted per versions. (read only)


You can combine the above parameters with the parameter `fields`. This way you can control the output. For example to get the `mainfile` for jQuery you would run the following request.

```
http://api.jsdelivr.com/v1/jsdelivr/libraries?name=jquery&fields=mainfile
```


It's possible to set multiple fields using a comma for separation.

```
http://api.jsdelivr.com/v1/jsdelivr/libraries?name=jquery&fields=mainfile,name
```

Get hosted files per version for jQuery
```
http://api.jsdelivr.com/v1/jsdelivr/libraries?name=jquery&fields=assets
```

Get hosted files for a selected version
```
http://api.jsdelivr.com/v1/jsdelivr/libraries/jquery/2.0.3
```

