# Create a yarn project.

These are my notes to read after you have completed the steps in the README file.

Let's compare creating a yarn project vs creating an npm project.
- Go to the `npm_proj` directory and execute `npm init`
 - Don't enter anything for name, descriptoin, entry point or test command. Just hit enter.
- Go to the `yarn_proj` directory and execute `yarn init`
 - Don't enter anything for the name, description, or entry point. Just hit enter.
- Compare the output of both files: `cat npm_proj/package.json && cat yarn_proj/package.json`
  - When done you can compare your notes to mine in the file "README-LAST.md"

```sh
➜  1_create_project git:(master) ✗ cat npm_proj/package.json
{
  "name": "npm_proj",
  "version": "1.0.0",
  "description": "Description of your project pulled from the README",
  "main": "unusual-starting-point.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "gangstead",
  "license": "MIT"
}
➜  1_create_project git:(master) ✗ cat yarn_proj/package.json
{
  "name": "yarn_proj",
  "version": "1.0.0",
  "description": "desc",
  "main": "index.js",
  "author": "gangstead",
  "license": "MIT"
}
```
Some notes:
- They are basically the same.  
- NPM asks about testing and starts a `scripts` section of your `package.json`.  If you don't specify anything it will make a place holder with a failing return value - a gentle reminder.  If you run `npm init` on a project that
- NPM checks in the directory and makes some intelligent guesses.
 - If there is a README file NPM will try to pull the description from there.
 - If there is only one `.js` file NPM will assume you want that for the entrypoint.  Yarn will look for `index.js` or `server.js` but defaults to `index.js` for anything else.
- Other than that they ask the same questions and create the same file, but NPM's init process is more refined.  
- NPM and Yarn are two different implementations but they are doing the same things and at run time Node doesn't care which one set up the project for you.  The NPM one is
