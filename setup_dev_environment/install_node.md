# Install Node.js

Installing Node.js is a straightforward process for most systems. On any platform, you can install Node.js using one of their pre-built installers available at [http://nodejs.org/](http://nodejs.org).

**Please Note:** Mac users should use Homebrew to install Node.js. DO NOT use the Node.js installer on a Mac unless you know what you're doing.

To install Node.js, simply download the installation package for your platform and install it like any other application.

However, for each operating system, you may consider an additional or alternative process.

## Linux Considerations

Linux \(or Unix\) users may use whatever package manager they prefer to install Node.js. Node.js is generally available on all Linux/Unix package management systems.

## Windows Considerations

Windows users may consider also installing the useful [CMDER](http://cmder.net/) tool, which adds a lot of functionality to the default Windows command line terminal. This includes basic Unix commands that are missing by default from Windows as well as nicer coloring and prompts so you can have a more effective interface.

Since we will spend a lot of time on the command line during this project, it will be nice to have a better terminal experience. If you are using CMDER, you will probably want to [read this article](https://www.awmoore.com/2015/01/14/setting-up-git-and-cmder/) to complete your setup.

## Mac Considerations

Mac users should use [Homebrew](http://brew.sh) to manage packages like Node.js \(and many other development tools\). Homebrew is a popular package management tool for Mac and it makes installing many packages much easier. The Homebrew website \([http://brew.sh](http://brew.sh)\) has a great installation tutorial to follow. Once you've installed Homebrew on your system, you can install Node.js with one command:

```
brew install node
```

Once that command completes successfully, you should have Node.js up and running on your Mac.

**If you install Node.js using the installer on a Mac then it will likely lead to permissions errors later on and require you to use **`sudo`** way too much. Please use Homebrew to install Node.js on a Mac.**

