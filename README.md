# lansa [![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Dependency Status][daviddm-image]][daviddm-url]
> CLI project deployment tracker


## Install

```sh
$ npm install --global lansa
```

## CLI Usage

## Project Usage

First and foremost, you need to define a `.lansarc` file in the root of your project configuration. This file defines details around the project and the various environments to which is is being deployed. Typically, these environments will each have their own Name and API key within NewRelic.

```js
{
	"app": {
		"projects": {
		    "{{project name}}": {
		        "production": {
		            "name"       : "Application Name in New Relic",
					"nrid"       : "Application ID in New Relic",
					"api_key"    : "User API Key in New Relic"
		        },
		        "staging"   : {
		            "name"       : "Application Name in New Relic",
					"nrid"       : "Application ID in New Relic",
					"api_key"    : "User API Key in New Relic"		        
		        }
		    }
		}
	}
}
```

This configuration will allow for multiple projects to be deployed from the same codebase to various New Relic dashboards. At least one project is required with at least one environment. Either a `name` or `nrid` is required. The `api_key` field is also required.

Once defined, a deployment can be tracked in New Relic by invoking Lansa at the command line:

```sh
lansa {{project name}}:environment -d "Description" -c "Changelog" -r "Revision ID" -u "User"
```

All command line flags except for the changelog are required.

## License

MIT © [Eric Mann](https://eamann.com)


[npm-image]: https://badge.fury.io/js/lansa.svg
[npm-url]: https://npmjs.org/package/lansa
[travis-image]: https://travis-ci.org/ericmann/lansa.svg?branch=master
[travis-url]: https://travis-ci.org/ericmann/lansa
[daviddm-image]: https://david-dm.org/ericmann/lansa.svg?theme=shields.io
[daviddm-url]: https://david-dm.org/ericmann/lansa
