# Ruby-Install

## Xcode (OSX)
Let's start with Xcode. The Xcode command line tools are a requirement for installing the homebrew package manager in the next step.

```
xcode-select --install
```

To conclude the installation you will need to agree to the Xcode license. Start the Xcode app, click "Agree", and allow the installation to finish. Then you can go ahead and quit the Xcode app.

## Homebrew (OSX)
Homebrew is kind of like a low-tech App Store. It allows us access to and the ability to install a wide variety of software and command line tools from the console. These are distinct from those hosted on the App Store and will need to be managed by Homebrew.

Go to: [brew.sh](https://brew.sh/)

## Git (optional)
Git is a version control system that allows us to track, commit and revert changes to files within a directory. Here we will install it and add global user info.

```
# install git
brew install git

# makes git terminal output pretty
git config --global color.ui true

# this will mark you as the 'author' of each committed change
git config --global user.name "your name here"

# use the email associated with your GitHub account
git config --global user.email your_email_here
```

# Ruby
Here we will be setting up Ruby with the help of rbenv, a Ruby environment manager. We like rbenv because it allows us to switch between versions of Ruby easily and setup default versions to use within project directories. This will install instances of Ruby in addition to the system version, which comes pre-installed.

## Rbenv + Ruby
First we will install rbenv, then use it to install our desired version of Ruby.

```
# install rbenv
brew install rbenv

# add to the PATH (rbenv commands are now available from terminal)
# .bashrc is the file that contains all of our terminal settings
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc

# initialize rbenv everytime you open a new console window 
echo 'eval "$(rbenv init -)"' >> ~/.bashrc

# update current console window with new settings
source ~/.bashrc

# source .bashrc from .bash_profile (necessary on some machines)
echo 'source ~/.bashrc' >> ~/.bash_profile

# install Ruby version 2.3.1
rbenv install 2.3.1

# set version 2.3.1 to be our global default
rbenv global 2.3.1

# the 'rehash' command updates the environment to your configuration
rbenv rehash

# and let's verify everything is correct
# check the version
ruby -v # => 2.3.1

# check that we are using rbenv's version of ruby
which ruby # => /Users/your-username/.rbenv/shims/ruby
```

## Gems
There are a few gems we will want to access globally.

* Bundler allows us to define project dependencies inside a `Gemfile` and gives us a bunch of commands to update, remove and install them. Check out the [Bundler docs](https://bundler.io/docs.html) for more info.
* Pry is an alternative to the Irb (the default Ruby REPL). It is not only more powerful, but also easier to use than Irb and should be your go-to for running and debugging Ruby code. Check out the [Pry website](http://pryrepl.org/) for more info and a super useful tutorial.
* Byebug is feature-rich debugging tool for Ruby. With Byebug you can halt the execution of your code and inspect/track variables and the flow of execution. Lots of cool features in here, so check out the [Byebug docs](https://github.com/deivid-rodriguez/byebug)!

**Run:**
```
gem install bundler pry byebug
```