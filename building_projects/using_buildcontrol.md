# Using `grunt-build-control`
Now that you have installed and configured `grunt-build-control` in your project, you can deploy your site to Github Pages for all the world to see. Huzzah!

## Review and commit your changes
In order to help you maintain a somewhat more sane approach to deploying your projects, `grunt-build-control` will not work when you have outstanding changes to files that are part of your repository. In order to deploy your work, you will need to commit all of your changes.

(NOTE: If you need a refresher on how to do this, refer to the [Git Reference](appendix/git_reference.md) in the appendix.)

## Build your project
Build the latest version of your project using the `build` task:

```
grunt build
```

This will update all the files in our `dist/` directory with the latest changes. 

## Deploy your project
Now you are ready to deploy. Run the `buildcontrol` task to deploy:

```
grunt buildcontrol
```