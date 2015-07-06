# Git Quick Reference
Throughout this book it is assumed that you have basic Git knowledge and skills. If you are new to Git (or if you just rarely use certain commands) it can be tough to remember all the steps and commands involved. There are many great resources for learning Git, and you are encouraged to go study until you feel comfortable with Git as a tool.

Until then, feel free to consult below.

**Please Note:** These directions refer to command line Git. If you are using a graphical Git interface, then you should be able to follow the same basic patterns and approaches described below, but you may have different names for some of these commands (or combinations of commands). Refer to the documentation for your preferred Git client.

## Committing and pushing
Whenever you finish a chunk of work that has any kind of meaning at all (a good stopping place, a completed component, etc.), you should make a commit. Think of commits as snapshots of your project at a specific time: You can always roll back to that exact state as long as there was a commit. These are the "mile markers" of our process, and we can always return to each step along the way.

### The commit process
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

### Pushing your work
Committing is only half the battle when it comes to sharing your work with others (or publishing your work online). You also need to "push". The command `git push` pushes your repository to a "remote". By default, when you clone a repo the server you cloned the repo from is labelled `origin`. You can push back to the origin with the command:

```git push origin```

Once you've pushed your work, it should show up on your Github repository homepage. Review the information on that page and you should see it show up.

There are many more aspects to pushing code. You can define as many remote servers as you wish and push code independently to each one. It's also possible to set up various rules for how branches get pushed and to associate local branches with remote branches, etc. All of these details are more advanced than we need for our work here, but you are encouraged to explore them as you need them.

## Branching and merging
When working with Git, it's often useful to use separate branches to contain work in progress or experimental features. This is especially useful when you are working on a project with others (you would typically keep your work in one branch until it's ready to combine with everyone else's work in the main branch). 

Although branching and merging is another area where Git can become quite complex and subtle differences can matter, you can get a lot of value from these features with a base knowledge of how to use them.

### Make a new branch
To make a new branch, you use the `git checkout` command with the `-b` flag like this:

```git checkout -b new-branch-name```

This will create a new branch based on whatever your current branch is (probably `master` in our case), and then it will `checkout` that branch so you will be "in" the `new-branch-name` branch. You may now edit files in this branch.

As you edit and modify files, you will need to commit your work like normal before switching to other branches. If you switch to another branch *without* committing your work, you may cause yourself problems, so be sure to keep a close eye on which files you've changed as you switch between branches.

To commit your work in a specific branch, you follow the exact same steps outlined above (just make sure you're in the branch you wish to commit to):

1. Stage your files.
2. Make a commit with a message.

This will make the commit to the `new-branch-name` branch. If you switch back to your `master` branch, you will see that whatever changes you made do not exist in the `master` branch.

**Please Note:** If you `push` the changes to your `new-branch-name` there is a good chance that when you run `git push origin` it will automatically push those changes to the `master` branch (since that is the branch we based `new-branch-name` on). This is often a very **bad** situation: We do not want to accidentally alter `master` when we mean to only share our working branch, `new-branch-name`. 

To avoid the issue described above, you must tell Git to make a new remote branch when you `push`:

```git push -u origin new-branch-name:new-branch-name```

That command tells Git to push your code. This command reads like so: First, we invoke `git`. Then we tell it we are using the `push` command. We use the `-u` flag so that it updates our local copy of the repository with the information we are giving it in this command.

The information we're giving it is that we are specifying the `origin` as the remote server. At the end of the command we also specify that we are pushing `new-branch-name` and we want to push it to the remote branch `new-branch-name`. (That is specified by the repetition of the name with the colon at the end of the line.) If the remote branch doesn't exist, then Git will create it with this push.

Once you've used that command, you can view your repository on Github and see that the new remote branch has been created.

### Change to different branches
To switch between branches you use the `checkout` command:

```git checkout branch-name```

Remember that you should commit your changes in your current working branch before switching to another branch.

### Merge two branches
To merge two branches, you use the `merge` command:

```git merge branch-name```

For example, if you had completed work on your new feature in the `new-branch-name` branch, you could merge that into your `master` branch with these steps:

1. Commit all your work in the `new-branch-name` branch.
2. Checkout the `master` branch.
3. Run `git merge new-branch-name` to merge the `new-branch-name` branch into the `master` branch.

At that point, Git would work to combine the changes from the `new-branch-name` branch into the `master` branch. If it runs into trouble figuring out which changes should stay (if, for example, the same lines of a file were modified in both `master` and `new-branch-name` branches), then Git will raise a "merge conflict".

### Handling merge conflicts
Merge conflicts happen invariably throughout development. Usually they are fairly simple to resolve, and work strategies that help keep your merge conflicts simple to resolve are generally preferred. That means keeping work in small chunks, constantly moving little improvements out of working branches and into the main branches of your project so everyone has the latest code. 

When merge conflicts do come up, you will receive a message in your console like this:

```bash
git status
# # On branch new-branch-name
# # You have unmerged paths.
# #   (fix conflicts and run "git commit")
# #
# # Unmerged paths:
# #   (use "git add ..." to mark resolution)
# #
# # both modified:      index.html
# #
# no changes added to commit (use "git add" and/or "git commit -a")

```
This message is telling you that there is a merge conflict in the `index.html` file. The trouble is that it has been modified in both branches you are dealing with, so Git cannot tell which changes should stay and which should go.

Git is asking you to fix ("resolve") the merge conflict and then add and commit those changes to make a new commit. Since Git bases everything on commits, it wants to make a commit once this conflict is resolved so it has a good point of reference going forward.

If you open `index.html` you may find something like this:

```html
Please
<<<<<<< HEAD
sign up!
=======
register now!
>>>>>>> new-branch-name
```

These can be a headache to look at, but they are very sensible if you read carefully. The `<<<<<<< HEAD` marker indicates the beginning of the content that was already in your current branch (in this example, `master`). There could be many lines of code, or just a few characters.

After that content is the `=======` line, which indicates the break between the code that was already in the current branch and the code from the new branch you are trying to merge in. Below the `=======` line is all that code from `new-branch-name`. 

Finally, the `>>>>>>> new-branch-name` marker indicates the end of the code coming in from the new branch. 

It is your job as the developer to decide what is right or wrong. You should correct it so that it reads like you'd prefer to see it:

```html
Please register now!
```

Be sure to remove all of the marker lines so they don't linger in your file and cause headaches later. Once you've finished, you should make a new commit by staging the files you fixed and committing them with a message.

**Please Note:** There can be more than one location in a file where there is a merge conflict. It is a good idea to use the "find" feature of your text editor to find sequences of "<<<" or ">>>" to make sure you cleaned up all those conflict markers.

## Useful tips for configuring Git