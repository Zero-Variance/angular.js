Steps to build the patched version (Windows)
=========

1. Switch to Node 16

nvm use 16.x.x

2. Add these resolutions in package.json:

```
"resolutions": {
    "//1": "`natives@1.1.0` does not work with Node.js 10.x on Windows 10",
    "//2": "(E.g. see https://github.com/gulpjs/gulp/issues/2162 and https://github.com/nodejs/node/issues/25132.)",
    "natives": "1.1.6",
    "//3": "`graceful-fs` needs to be pinned to support gulp 3, on Node v12+",
    "graceful-fs": "^4.2.3",
    "commander": "2.20.3",
    "selenium-webdriver": "3.6.0"
  },
```

3. Clean dependencies

```
del .\package-lock.json
del .\yarn.lock  
del .\node_modules\
```

4. Remove changez

```
yarn remove changez
```

5. Install dependencies:

```
yarn install --ignore-engines --ignore-optional
```

6. Switch to Node 20

```
nvm use 20.x.x.
```

7. Build the package

```
yarn grunt build
```
