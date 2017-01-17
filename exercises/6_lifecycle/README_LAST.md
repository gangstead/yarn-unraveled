# Lifecycle scripts

NPM has many pre defined scripts that will run automatically.

One common one is the `postinstall` script.  This is useful if there is something that needs to be done after a script is installed, such as compiling a plugin that is not written in Node.  It is also a huge security vulnerability as it will execute anything you tell it to.

- I've created a simple package with an even simpler postinstall script that logs a message to the console: https://github.com/gangstead/npm-postinstall
- Install it with npm: `npm install gangstead/npm-postinstall` and observe the output
- Uninstall it `rm -f node_modules`
- Install it with yarn `yarn add gangstead/npm-postinstall` and observe the output

- NPM also automatically runs any `pre[X]` and `post[X]` scripts when you run a script with `npm run [X]`.  Yarn does this behavior as well.
- Try running `npm run test` (same as `npm test`)
- Then try running `yarn run test` (same as `yarn test`)

Notes:
My console output from running these commands:
```sh
➜  6_lifecycle git:(master) ✗ npm install gangstead/npm-postinstall

> npm-postinstall@1.0.0 postinstall /Users/gangstead/code/yarn-unraveled/exercises/6_lifecycle/node_modules/npm-postinstall
> echo "----------------------------------
Post Install Script worked!"

----------------------------------
Post Install Script worked!
6_lifecycle@1.0.0 /Users/gangstead/code/yarn-unraveled/exercises/6_lifecycle
└── npm-postinstall@1.0.0  (git://github.com/gangstead/npm-postinstall.git#9995d5d1d39e4444e94dcb97a1f265bc9a8c55ff)

npm WARN 6_lifecycle@1.0.0 No description
npm WARN 6_lifecycle@1.0.0 No repository field.
➜  6_lifecycle git:(master) ✗ rm -r node_modules
➜  6_lifecycle git:(master) ✗ yarn add gangstead/npm-postinstall
yarn add v0.19.1
info No lockfile found.
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 📃  Building fresh packages...
success Saved lockfile.
success Saved 1 new dependency.
└─ npm-postinstall@1.0.0
✨  Done in 1.75s.
```

This may be intended behavior: https://github.com/yarnpkg/yarn/issues/853 .  But it also may just be a bug.  This PR was merged in October 2016 but hasn't made it to a release as of January 2017: https://github.com/yarnpkg/yarn/pull/800

- `pre` and `post` scripts still run the same in NPM and Yarn:
```sh
➜  6_lifecycle git:(master) ✗ npm run test

> 6_lifecycle@1.0.0 test /Users/gangstead/code/yarn-unraveled/exercises/6_lifecycle
> echo "This is the test script"

This is the test script

> 6_lifecycle@1.0.0 posttest /Users/gangstead/code/yarn-unraveled/exercises/6_lifecycle
> echo "This is the POST test script"

This is the POST test script
➜  6_lifecycle git:(master) ✗ yarn run test
yarn run v0.19.1
$ echo "This is the test script"
This is the test script
$ echo "This is the POST test script"
This is the POST test script
✨  Done in 0.25s.
```
