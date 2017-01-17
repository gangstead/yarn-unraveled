# Time Trials

Yarn installs your dependencies faster, but how fast is faster?

Try these commands from the project in this directory:
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


## Bonus Yarn feature
- `yarn install --flat`

Note: the dependencies in this `package.json` are similar to the basic set up of many of our Node microservices at Vinli.
