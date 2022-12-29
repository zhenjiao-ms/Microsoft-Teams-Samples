# Steps to migrate to teamsfx

## Goal
- No change of source code
- Support 1-click debugging

## Must be done
1. teamsfx init debug, select "node" and "tab"
2. Update Manifest/manifest.json, replace the variables
3. Update app.local.yml to replace manifest file path
## For https
4. Update task.json to dd the task "Start local tunnel"
5. Update the variables for endpoint/domain in manifest file
## Enable debug
6. Add ```    "dev": "nodemon --inspect=9239 --signal SIGINT server.js",``` to package.json
7. Update teamsfx/script/run.js to change ```["run", "start"]``` to ```["run", "dev"]```
8. Add the following to app.local.yml
```
  - uses: cli/runNpmCommand
    with:
      args: install -D nodemon
```
9. Add listening to task.json to be ```"endsPattern": "Compiled|Failed|compiled|failed|listening"```

**Issue: still cannot set breakpoint**

## Change port
10. Update the port from 53000 to 3978 in the following files
    1. teamsfx/script/run.js
    2. task.json
## To set env variables of the app

n/a
