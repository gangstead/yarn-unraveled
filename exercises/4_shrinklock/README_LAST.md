# Shrinkwrap vs Lock

NPM has always had Shrinkwrap files to lock in dependencies while Yarn has lock files.

- First run `npm install` to get all the dependencies
- Then run `npm shrinkwrap`

### NOTES:
- `npm shrinkwrap` works on the contents of the `node_modules` directory, so if you are manually editing `package.json` without `npm install`-ing then the shrinkwrap json will not be in sync.
- It's nice that the shrinkwrap file is json so it's easier to parse through if you want to automate doing something with it.  Yarn's `lock` file syntax is a little more readable and also makes it easier to see where a dependency is being brought in (useful for finding dependencies of your dependencies)
- If you are not deploying in containers then locking down your version files is essential and yarn is going to be much better for you since it is making the lock files automatically.
- When your versions are locked down you are not going to get patch updates which are generally a good thing to get
 - For example if your version of lodash in your `package.json` is `^4.17.3` because 4.17.3 was the latest version when you installed.  Your yarn.lock file is going to look like this:
 ```
 lodash@^4.17.2, lodash@^4.17.3:
  version "4.17.3"
  resolved "https://registry.yarnpkg.com/lodash/-/lodash-4.17.3.tgz#557ed7d2a9438cac5fd5a43043ca60cb455e01f7"
```
 - When lodash 4.17.4 is released if you do `yarn install` you are not going to get it.  This could be a good thing or a bad thing.  Accidents happen and sometimes patch releases break things, but it's lot less intimidating to try the latest patch release of lodash as part of your regular builds than put off upgrading and then needing to go from 4.17.3 to 4.50.20 in one big jump.  What you don't want to do (and a lock / shrinkwrap file can help with) is trying that new version of lodash for the first time in production.  
 - At Vinli we have good unit test coverage and our CI does a fresh npm install on every build.  If it passes then the entire application is checked in as a container.  If it fails because a freshly released package breaks something, and this does happen, it's usually pretty trivial to see what was just published, and try to submit a fix or pin that one version down in the package json temporarily.  We prefer having these small pains as we go along than letting patches build up as tech debt that no one is ever going to get around to fixing.
