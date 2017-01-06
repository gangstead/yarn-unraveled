# Time Trials

**TODO: add some dependencies**
**TODO: add some dependencies**

Yarn installs your dependencies faster
- Clear your cache in your `~/.npm` folder and install this package.
  - `rm node_modules && npm cache clean && time npm install`
- When run a second time modules should be cached and installation should be faster:
  - `rm node_modules && time npm install`
- Compare this with yarn:
  - `rm node_modules && yarn cache clean && yarn install`
- And when yarn's cache is warm:
  - `rm node_modules && yarn install`


## Bonus Yarn feature
- `rm node_modules && yarn install --flat`
- 
