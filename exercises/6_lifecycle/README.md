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

Notes in README_LAST.md
