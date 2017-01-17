# Shrinkwrap vs Lock

NPM has always had Shrinkwrap files to lock in dependencies while Yarn has lock files.

- First run `npm install` to get all the dependencies
- Then run `npm shrinkwrap`
- Then run `yarn install`
- Compare `npm-shrinkwrap.json` to `yarn.lock`
