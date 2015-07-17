# Install `generator-angular`
Just as we installed the `generator-webapp` previously, we must first install the Yeoman generator for making AngularJS project skeletons. Installing the AngularJS generator is just like installing any Node.js module. You may consult [the NPM package page for `generator-angular`](https://www.npmjs.com/package/generator-angular) for further details about the generator.

```bash
npm install -g generator-karma generator-angular
```

If you already have these generators installed, be sure to update them:

```bash
npm update -g generator-karma generator-angular
```

Once that process has finished successfully, you are ready to move on. 

## A little more about `generator-angular`
The AngularJS project generator contains support not just for generating a brand new project, but also for building new components of a project as you work on it. This is useful for keeping projects in order, and also for helping novice developers make quicker progress on project builds. 

Consult [the `generator-angular` NPM package page](https://www.npmjs.com/package/generator-angular) for more information about all of the commands the generator offers, and be aware that we will use those commands as we work through building out our project here. When you see those `yo angular:<command>` commands come along, that's what is happening: We are using the generator to generate a new component of our existing project.

**Note:** Some of you, dear readers, may have learned about the problems that can be caused when generating a project inside of a project. The reason that causes problems is that in order to facilitate features like `generator-angular` makes use of, Yeoman looks in the parent directories for a project definition. When it finds one, it tries to run the command as part of the existing project. Needless to say, if you're not running a command that works within the existing project, you will see problems.