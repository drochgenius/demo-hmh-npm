# demo-hmh-npm
Demo HMH private npm registry

# HMH Private NPM Registry

http://npm.tribalnova.com

* Meant to install/publish packages under the `@hmh` scope.
* Service available only within HMH VPN
* No authentication required
* Powered by [Verdaccio](https://verdaccio.org/).

## Getting Started

Run the following command once in a lifetime to setup the registry on your computer:

```shell
npm config set @hmh:registry http://npm.tribalnova.com
```

From this point on, any packages with `@hmh` scope will resolve to this registry.

## Publishing packages

Prior to publishing your first package, you must run the following command once:

```shell
npm adduser --registry http://npm.tribalnova.com
```

**Enjoy!**


## Additional Notes

### Fallback on RCE NPM Registry 

This registry is configured to fallback on the old Sinopia-based RCE NPM Registry hosted in Dublin: http://172.17.101.192:4873.
This means, any missing `@hmh`-scoped packages will also be looked up on the RCE NPM Registry, and if the package cannot be found in neither of those registry it fails. 

There is also a caching strategy, so packages hosted on RCE registry get automatically cached in the new registry.

### Who uses this NPM Registry

* Dublin CPL and Content teams
* Dublin RCE team
* Montreal

### Can we migrate the package data?

Yes, package data is currently stored on Amazon EFS in a single folder. If ever we wanted to transfer the package data to another registy, e.g. on Bedrock, it's failry easy to do.