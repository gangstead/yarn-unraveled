# Install Dependencies

**TODO: Find some specific versions of dependencies that highlight this problem**

Yarn claims its builds are deterministic.  What does that mean?

Start with a package json with these dependencies
(Source: https://docs.npmjs.com/how-npm-works/npm3-nondet)
```json
"dependencies": {
  "mod-a": "^1.0.0",
  "mod-c": "^1.0.0",
  "mod-d": "^1.0.0",
  "mod-e": "^1.0.0"
}
```

See what happens in NPM when you add your dependencies one-by-one while you are developing and then if you install them all at once:
- `cd npm_proj`
- `npm install`
- `npm install mod-a@2 --save`
- `npm ls`
 - Observe the tree it prints out
- `rm -r node_modules && npm install`
 - Observe the tree it prints out

Now do the same steps with yarn:
- `cd yarn_proj`
- `yarn install`
- `yarn add mod-a@2`
- `yarn list`
 - Observe the tree it prints out
- `rm -r node_modules yarn.lock && yarn install`
- `yarn list`
 - Observe the tree it prints out
