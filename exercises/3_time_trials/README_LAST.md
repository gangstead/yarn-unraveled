# Time Trials

Yarn installs your dependencies faster
- Clear your cache in your `~/.npm` folder and install this package.
  - `rm -r node_modules && npm cache clean && time npm install`
- When run a second time modules should be cached and installation should be faster:
  - `rm -r node_modules && time npm install`
- Compare this with yarn:
  - `rm -r node_modules && rm yarn.lock && yarn cache clean && time yarn install`
- And when yarn's cache is warm:
  - `rm -r node_modules && rm yarn.lock && time yarn install`
- And when yarn's cache is warm and your lock file is already present:
  - `rm -r node_modules && time yarn install`

### Reference times
*Obviously these times will be different on your computer and internet connection than mine:*
*Average time for 3 executions*
- NPM clean install: 23.920s
- NPM install from cache: 16.589s
- Yarn clean install: 8.408s
- Yarn warm cache, no lock file: 4.939s
- Yarn warm cache, lock file present: 3.883s


## Bonus `yarn install --flat`
- The first time you run with the `--flat` flag you will be forced to make some difficult choices.
  - For example:

```sh
info Unable to find a suitable version for "lodash", please choose one by typing one of the numbers below:
  1) "lodash@^4.17.4, lodash@^4.17.2, lodash@^4.0.0, lodash@^4.3.0" which resolved to "4.17.4"
  2) "lodash@^3.10.0" which resolved to "3.10.1"
Answer?: 1
```
  - You'll have to go back and read the docs and find out that lodash had a ton of major changes [between 3 & 4](https://github.com/lodash/lodash/wiki/Changelog#v400).
- After you make your choices they will be added under a `resolutions` section of `package.json`
- Example:

```json
"resolutions": {
  ...
  "lodash": "4.17.4",
  ...
}
```
- In your flattened lock file you will see
```sh
lodash@^3.10.0, lodash@^4.0.0, lodash@^4.17.2, lodash@^4.17.4, lodash@^4.3.0:
  version "4.17.4"
  resolved "https://registry.yarnpkg.com/lodash/-/lodash-4.17.4.tgz#78203a4d1c328ae1d86dca6460e369b57f4055ae"
```
- Previously in the non-flat lock file you will see:

 ```sh
 lodash@^3.10.0:
   version "3.10.1"
   resolved "https://registry.yarnpkg.com/lodash/-/lodash-3.10.1.tgz#5bf45e8e49ba4189e17d482789dfd15bd140b7b6"

 lodash@^4.0.0, lodash@^4.17.2, lodash@^4.17.4, lodash@^4.3.0:
   version "4.17.4"
   resolved "https://registry.yarnpkg.com/lodash/-/lodash-4.17.4.tgz#78203a4d1c328ae1d86dca6460e369b57f4055ae"
 ```
- I think for `--flat` to be useful your dependencies have to be simple, not very deep, and very few in number otherwise you are going to have to know them very well.  I'm not sure what the benefit of flat dependencies are other than smaller disk space.  SemVer usually works very well in the Node ecosystem.  There is generally an agreement on what constitutes patch/minor/major versions and they are usually respected, especially in the more popular packages.
