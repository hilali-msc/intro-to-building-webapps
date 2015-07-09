# Configure `grunt-build-control`
In order to use `grunt-build-control` you will need to configure it. This process involves configuring a JSON object to define the options and settings we wish to use for our project.

**Please Note:** `grunt-build-control` can be used to deploy to a variety of places. We are only going to explore one method of configuring this tool. Be aware that you may be able to use this tool for other purposes, too.

## Configure the `buildcontrol` task
In order to use `grunt-build-control`, it's necessary to create a JSON object to configure the task. The order of your tasks in the `grunt.initConfig()` doesn't matter, but it's important you do not break another task configuration. To keep things easy, I advocate placing this definition right before the definition for the `watch` task (which is what Grunt uses to know when you've changed files when you are running the local server).

This should looks something like this:

```js
  // Define the configuration for all the tasks
  grunt.initConfig({

    // Project settings
    config: config,

    buildcontrol: {
      options: {
        dir: 'dist',
        commit: true,
        push: true,
        message: 'Built %sourceName% from commit %sourceCommit% on branch %sourceBranch%'
      },
      pages: {
        options: {
          remote: 'git@github.com:your_github_user/your_webapp.git',
          branch: 'gh-pages'
        }
      }
    },

    // Watches files for changes and runs tasks based on the changed files
    watch: {
    
    ... more code ...
```

Let's look more closely at the configuration we just specified. First, we define general `options` for the `buildcontrol` task to use every time it runs: It will build to the `dist` directory. It will make a commit inside that directory and push it if need be. The message it uses in the commit will be the one specified above.

In addition to these general options, we can specify specific build targets. In this case, we are defining `pages` as our only target. We could define multiple targets if we needed. (For example, you may have a staging site and a production site. In that case, you could define to `buildcontrol` build targets: one for `staging` and one for `production`.)

For our purposes, we want to specify the remote server (using the SSH URL that Github gives us) and the remote branch (`gh-pages`, of course). This tells the `buildcontrol` task that it should deploy the results of the build process to our `gh-pages` branch. Once that happens, Github will automatically make that `gh-pages` branch available to the public.

**Be sure to update the `remote` value with the SSH URL to your own repository.**

Once you've added this configuration to your project, you may proceed to deploy your project on Github Pages.