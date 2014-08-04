aBird.co
===============

[![Build Status](https://travis-ci.org/aichholzer/aBird.co.svg)](https://travis-ci.org/aichholzer/aBird.co)
[![Dependencies](https://david-dm.org/aichholzer/aBird.co.png)](https://david-dm.org/aichholzer/aBird.co)

[![NPM](https://nodei.co/npm/abird.co.png?downloads=true&stars=true)](https://nodei.co/npm/abird.co/)

[![NPM](https://nodei.co/npm-dl/abird.co.png)](https://nodei.co/npm/abird.co/)

Simple wrapper for the aBird.co API -The world's most awesome URL shortening service. Please make sure you visit (and read) [http://docs.abird.co](http://docs.abird.co) for response specific details.

Using this module can't be made any easier:

Install aBird.co

```
npm install abird.co
```

Require aBird.co

```
var abird = require('abird.co').fly(options);
```

The `options` object may contain:

* `env` - Which environment is being used; `PRO` or `DEV`. Defaults to `PRO`.
* `apiKey` - Your API key, obtained from your [aBird.co](https://account.aBird.co) profile page. Providing an API key is only required when using the `shrink` method.
* `timeout` - API request timeout, in milliseconds. Defaults to `3600`. 


And you are ready to use this awesome API.

```
The examples listed in this document assume that Express is being used.
```

#### Shrink a URL

```
var url = 'https://github.com/aichholzer/aBird.co';
abird.shrink(url, [mask -optional], function(err, data) {
	if (err) {
		return next(err);
	}

	res.send(data);
});
```


#### Expand a URL

```
var url = 'http://ab.je/a';
abird.expandFromURL(url, function(err, data) {
	if (err) {
		return next(err);
	}

	if (!data) {
		res.send(404);
	} else {
		res.redirect(302, data.url);
	}
});
```


#### Expand a hash

```
var hash = 'a';
abird.expandFromHash(hash, function(err, data) {
	if (err) {
		return next(err);
	}

	if (!data) {
		res.send(404);
	} else {
		res.redirect(302, data.url);
	}
});
```


#### Delete a URL

```
var url = 'http://ab.je/a';
abird.delete(url, [type -optional], function(err, statusCode) {
	if (err) {
		return next(err);
	}

	res.send(statusCode);
});
```














