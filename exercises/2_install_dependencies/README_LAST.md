```sh
➜  npm_proj git:(master) ✗ npm install
deterministic@1.0.0 /Users/gangstead/code/yarn-unraveled/exercises/2_install_dependencies/npm_proj
├─┬ mod-a@1.0.0
│ └── mod-b@1.0.0
├─┬ mod-c@1.0.0
│ └── mod-b@2.0.0
├─┬ mod-d@1.0.0
│ └── mod-b@2.0.0
└── mod-e@1.0.0

➜  npm_proj git:(master) ✗ npm install mod-a@2 --save
deterministic@1.0.0 /Users/gangstead/code/yarn-unraveled/exercises/2_install_dependencies/npm_proj
└─┬ mod-a@2.0.0
  └── mod-b@2.0.0

➜  npm_proj git:(master) ✗ npm ls
deterministic@1.0.0 /Users/gangstead/code/yarn-unraveled/exercises/2_install_dependencies/npm_proj
├─┬ mod-a@2.0.0
│ └── mod-b@2.0.0
├─┬ mod-c@1.0.0
│ └── mod-b@2.0.0
├─┬ mod-d@1.0.0
│ └── mod-b@2.0.0
└─┬ mod-e@1.0.0
  └── mod-b@1.0.0

➜  npm_proj git:(master) ✗ tree -d node_modules
node_modules
├── mod-a
│   └── node_modules
│       └── mod-b
├── mod-b
├── mod-c
│   └── node_modules
│       └── mod-b
├── mod-d
│   └── node_modules
│       └── mod-b
└── mod-e

➜  npm_proj git:(master) ✗ rm -r node_modules && npm install
deterministic@1.0.0 /Users/gangstead/code/yarn-unraveled/exercises/2_install_dependencies/npm_proj
├─┬ mod-a@2.0.0
│ └── mod-b@2.0.0
├── mod-c@1.0.0
├── mod-d@1.0.0
└─┬ mod-e@1.0.0
  └── mod-b@1.0.0

➜  npm_proj git:(master) ✗ tree -d node_modules
node_modules
├── mod-a
├── mod-b
├── mod-c
├── mod-d
└── mod-e
    └── node_modules
        └── mod-b  
```


With yarn:
```sh
➜  yarn_proj git:(master) ✗ yarn install
yarn install v0.19.1
info No lockfile found.
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 📃  Building fresh packages...
success Saved lockfile.
✨  Done in 0.67s.
➜  yarn_proj git:(master) ✗ yarn list
yarn list v0.19.1
├─ mod-a@1.0.0
│  └─ mod-b@^1.0.0
├─ mod-b@1.0.0
├─ mod-c@1.0.0
│  ├─ mod-b@^2.0.0
│  └─ mod-b@2.0.0
├─ mod-d@1.0.0
│  ├─ mod-b@^2.0.0
│  └─ mod-b@2.0.0
└─ mod-e@1.0.0
│  └─ mod-b@^1.0.0
✨  Done in 0.21s.
➜  yarn_proj git:(master) ✗ tree -d node_modules
node_modules
├── mod-a
├── mod-b
├── mod-c
│   └── node_modules
│       └── mod-b
├── mod-d
│   └── node_modules
│       └── mod-b
└── mod-e

9 directories

➜  yarn_proj git:(master) ✗ yarn add mod-a@2
yarn add v0.19.1
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 📃  Building fresh packages...
success Saved lockfile.
success Saved 1 new dependency.
└─ mod-a@2.0.0
✨  Done in 0.60s.
➜  yarn_proj git:(master) ✗ yarn list
yarn list v0.19.1
├─ mod-a@2.0.0
│  ├─ mod-b@^2.0.0
│  └─ mod-b@2.0.0
├─ mod-b@1.0.0
├─ mod-c@1.0.0
│  ├─ mod-b@^2.0.0
│  └─ mod-b@2.0.0
├─ mod-d@1.0.0
│  ├─ mod-b@^2.0.0
│  └─ mod-b@2.0.0
└─ mod-e@1.0.0
│  └─ mod-b@^1.0.0
✨  Done in 0.19s.
➜  yarn_proj git:(master) ✗ tree -d node_modules
node_modules
├── mod-a
│   └── node_modules
│       └── mod-b
├── mod-b
├── mod-c
│   └── node_modules
│       └── mod-b
├── mod-d
│   └── node_modules
│       └── mod-b
└── mod-e

11 directories

➜  yarn_proj git:(master) ✗ rm -r node_modules yarn.lock && yarn install
yarn install v0.19.1
info No lockfile found.
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 📃  Building fresh packages...
success Saved lockfile.
✨  Done in 0.75s.
➜  yarn_proj git:(master) ✗ yarn list
yarn list v0.19.1
├─ mod-a@2.0.0
│  ├─ mod-b@^2.0.0
│  └─ mod-b@2.0.0
├─ mod-b@1.0.0
├─ mod-c@1.0.0
│  ├─ mod-b@^2.0.0
│  └─ mod-b@2.0.0
├─ mod-d@1.0.0
│  ├─ mod-b@^2.0.0
│  └─ mod-b@2.0.0
└─ mod-e@1.0.0
│  └─ mod-b@^1.0.0
✨  Done in 0.20s.

➜  yarn_proj git:(master) ✗ tree -d node_modules
node_modules
├── mod-a
│   └── node_modules
│       └── mod-b
├── mod-b
├── mod-c
│   └── node_modules
│       └── mod-b
├── mod-d
│   └── node_modules
│       └── mod-b
└── mod-e

11 directories
```

Further reading: https://docs.npmjs.com/how-npm-works/npm3-nondet

The take away is that if you add your dependencies as you go with `npm install [dependency] --save` and then someone else takes your completed package.json and does `npm install` they might end up with a different structure.  The dependencies might be resolved with different versions but still satisfy all of the SemVer requirements.  With yarn it does not matter.

In practice `rm -r node_modules && npm install` is deterministic.  You will get the same build every time.
