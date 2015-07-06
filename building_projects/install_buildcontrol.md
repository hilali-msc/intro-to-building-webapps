# Install `grunt-build-control`
The `grunt-build-control` component is a Node.js module you can install with `npm`. In order to install it, open your terminal and change directory to the root of your project repository. Run this command to install `grunt-build-control`:

```bash
npm install grunt-build-control --save-dev
```

That command tells `npm` to install the `grunt-build-control` package, and it also uses the `--save-dev` flag to tell `npm` to add this module to our `package.json` file (which is the file `npm` uses to track the Node.js modules we are using in this project). By using `--save-dev` we make sure that the next developer who clones this repo and installs the dependencies will get `grunt-build-control` alongside everything else.

The installation will finish with showing you the version of `grunt-build-control` that was installed and the dependencies it had:

```bash
grunt-build-control@0.5.0 node_modules/grunt-build-control
├── semver@4.3.6
└── shelljs@0.2.6
```

There is not much fanfare when you are successful here, but you will receive a message if `npm` runs into an error. Verify you have not received an error message (you don't need to worry about `npm` warnings about "description" or "repository field") and you can move on.