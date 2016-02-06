# Normandy Actions
This repository contains the implementations of actions used in the
[Normandy recipe server][normandy].

[normandy]: https://github.com/mozilla/normandy

## Actions
Actions are structured as subfolders under the `actions` directory. The name of
the directory is used as the name of the action when uploading, meaning that
they must be valid slugs (alphanumeric + underscore and dash).

An action is required to have two files: an `index.js` file implementing the
action, and an `arguments.json` file describing the arguments object that the
action accepts using [JSON Schema][].

The `index.js` file must call the global `Normandy.registerAction` function,
passing the name of the action (which must match the directory name) and a
function implementing the action. The function has two arguments:

1. The `Normandy` object, which provides access to certain privileged functions
   like highlighting elements in the Firefox chrome.
2. An `arguments` value that conforms to the schema in `arguments.json`. These
   allow actions to be reused in several recipes, with the arguments being
   filled in within the admin interface on the recipe server.

Actions are built using [Webpack][] and can be written in [ES2015][] thanks to
[Babel][]. See `.babelrc` for our specific configuration.

[JSON Schema]:
[Webpack]:
[ES2015]:
[Babel]:

## Scripts

### `npm run build`

Runs Webpack to build the actions.

### `npm run upload`

Uploads actions

```sh
npm run upload -- action-name other-action-name
```

## License

Normandy actions are licensed under the MPLv2. See the `LICENSE` file for
details.
