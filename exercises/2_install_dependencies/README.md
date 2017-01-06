# Install Dependencies

**TODO: Find some specific versions of dependencies that highlight this problem**

Yarn builds are deterministic.  What does that mean?
### Example with NPM
- Go to `npm_proj` and execute the following commands:
 - `npm install blah1`
 - `npm install blah2`
 - `npm install blah3`
- Now see what versions are installed with `npm list`
- Save the output of `npm list`
- Remove the installed dependencies by deleting the `node_modules` directory
- Now execute these commands:
 - `npm install blah3`
 - `npm install blah2`
 - `npm install blah1`
- Execute `npm list` again
- Compare the two outputs.  Why are they different?

### Example with Yarn
- Go to `yarn_proj` and execute the following commands:
 - `yarn add blah1`
 - `yarn add blah2`
 - `yarn add blah3`
- Now see what yarn has installed with `yarn ls`
- Remove installed dependencies by deleting the `node_modules` directory
- Now execute these commands:
 - `yarn add blah3`
 - `yarn add blah2`
 - `yarn add blah1`
- Execute `yarn ls` again
- Compare the two outputs.  They should be the same
