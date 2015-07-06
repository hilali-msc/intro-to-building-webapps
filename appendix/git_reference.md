# Git Quick Reference
Throughout this book it is assumed that you have basic Git knowledge and skills. If you are new to Git (or if you just rarely use certain commands) it can be tough to remember all the steps and commands involved. There are many great resources for learning Git, and you are encouraged to go study until you feel comfortable with Git as a tool.

Until then, feel free to consult below.

## Committing and Pushing
Whenever you finish a chunk of work that has any kind of meaning at all (a good stopping place, a completed component, etc.), you should make a commit. Think of commits as snapshots of your project at a specific time: You can always roll back to that exact state as long as there was a commit. These are the "mile markers" of our process, and we can always return to each step along the way.

### The Commit Process
When you commit you do two things: 

1. Add/remove files from the "stage". (This is called "Staging")
2. Once you're happy with what files have been "staged", commit them with a message. (This is called "Committing".)

#### Staging Files
To add your files to the stage, you can do so with varying degrees of specificity. It's generally best practice to be very specific and controlled when adding files to your stage for committing. A recommended process may look something like this:

Run `git status` to see what files have changes. This will return a list of files that have been altered or added.

Add each file you wish to include in the commit using the `git add` command like so:

`git add app/myfile.html`

If you have lots of files to add, such as several files altered within the `app/` directory, you can use wildcards to add files to the stage:

`git add app/styles/*`

If you know you want to commit all of the altered files (and you've reviewed what those are by running `git status`), then you can use the `-A` flag from the root of your project:

`git add -A`

That command will add all changed files in the repo to your stage.

#### Committing Files
Once you've staged your files, you can commit them. Whenever you commit, you must send a message along with your commit. You can configure which command line text editor is invoked when you commit, you can use a text file to store your commit message, or you can send the message along with the `-m` flag on the `git commit` command. 

It is best practice to send more than a one line commit message, especially whenever you're making a commit that you wish to be reviewed by others. However, many developers take a shortcut and add a message to their commit command. For the purposes of our work here, this should be fine.

Before you commit your changes, you should run `git status` and make sure that the correct files are staged for commit and nothing has been omitted or accidentally added. You can fix any issues using the instructions provided along with the `status` display.

Commit your changes with this command:

```git commit -m "YOUR MESSAGE HERE"```

You should receive a message letting you know you have successfully made a commit. You can review the commits in your project with the `git log` command, which will print a list of the commits in any project. Run `git log` and you should see your latest commit at the top of the list.

### Pushing Your Work
Committing is only half the battle when it comes to sharing your work with others (or publishing your work online). You also need to "push". The command `git push` pushes your repository to a "remote". By default, when you clone a repo the server you cloned the repo from is labelled `origin`. You can push back to the origin with the command:

```git push origin```


## Branching and Merging

## Useful Tips for Configuring Git