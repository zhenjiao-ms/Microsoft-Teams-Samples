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
## Fix hard-coded problem in teamsfx
6. Update task.json to add "listening" to endsPattern
7. Update the port from 53000 to 3978 in the following files
    1. teamsfx/script/run.js
    2. task.json
## To set env variables of the app

n/a
