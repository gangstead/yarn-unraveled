# Combined

Yarn tries to play nice with NPM, so you can experiment with Yarn in a project that has already been set up with NPM.

In this directory:
- `npm install --save commander`
- `yarn add lodash`
- What dependencies are in the `yarn.lock` file?

The interesting thing here is that the `yarn.lock` file includes the dependencies that were already in `package.json` before yarn created the lock file.

```sh
➜  5_combined git:(master) ✗ cat package.json
{
  "name": "3_time_trials",
  "version": "1.0.0",
  "main": "index.js",
  "author": "Gangstead",
  "license": "MIT",
  "dependencies": {
    "commander": "^2.9.0",
    "lodash": "^4.17.4"
  }
}
➜  5_combined git:(master) ✗ cat yarn.lock
# THIS IS AN AUTOGENERATED FILE. DO NOT EDIT THIS FILE DIRECTLY.
# yarn lockfile v1


commander@^2.9.0:
  version "2.9.0"
  resolved "https://registry.yarnpkg.com/commander/-/commander-2.9.0.tgz#9c99094176e12240cb22d6c5146098400fe0f7d4"
  dependencies:
    graceful-readlink ">= 1.0.0"

"graceful-readlink@>= 1.0.0":
  version "1.0.1"
  resolved "https://registry.yarnpkg.com/graceful-readlink/-/graceful-readlink-1.0.1.tgz#4cafad76bc62f02fa039b2f94e9a3dd3a391a725"

lodash@^4.17.4:
  version "4.17.4"
  resolved "https://registry.yarnpkg.com/lodash/-/lodash-4.17.4.tgz#78203a4d1c328ae1d86dca6460e369b57f4055ae"
```
