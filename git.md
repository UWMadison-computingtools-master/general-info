## why git?

track and share versions of a project.  
what does git do?

- you take snapshots of your project once in a while. one "commit" = one snapshot
- git stores the changes between snapshots, not the whole files
- git stores its data (changes) in a special `.git` directory
- you can easily restore the whole project to a previous snapshot, then
  get back to the latest snapshot
- each collaborator has the project on her/his local machine, and
  another remote copy of the project is on GitHub.
  Collaborators can "pull" from GitHub and "push" to GitHub.

Let's browse [this git repository](https://github.com/vibbits/phyd3),
click on:

- ["commits"](https://github.com/vibbits/phyd3/commits/master)
  near the top right:
  see changes, see commit "name" (sha, e.g. `04b4b47`),
  browse files at earlier time points
  (click on the `<>` button to the right, at any given prior time point)
- [insights > network](https://github.com/vibbits/phyd3/network):
  see a graphical representation of all commits and
  how they are related to each other
- [issues](https://github.com/vibbits/phyd3/issues?q=is%3Aissue):
  for discussions between collaborators, to track bugs, next steps,
  link fixes to commits, etc.

## install git

Check to see if it's already installed,
and check that your installation worked:
`which git` (tells you where the git program is) or
`git --version`(tells you which version you have) or
`git --help` or `man git` to get help.

- to install git on Mac OSX:
  I recommend using the homebrew package manager, because we will
  use homebrew to install many other utilities. The work to get
  homebrew is an investment that will make all other package installation
  easier for the rest of your computing work.
  * make sure you already installed the
    [Xcode](https://apps.apple.com/us/app/xcode/id497799835)
    developer tools: `xcode-select --install`
  * get [homebrew](http://brew.sh) if you don't have it already.
    check with `which brew`.
  * if you got homebrew a while ago, you should update and/or upgrade it:
    `brew update` and `brew upgrade`.
  * install git through homebrew: run `brew install git`

- to install git on Linux:
  * Ubuntu or Debian: use the package manager "apt" (advanced packaging tools)
    and run `sudo apt-get install git` (sudo = super-user do).
    You may want to run `sudo apt-get update` before, to update your
    list of packages & versions.
  * Fedora or RedHat: `sudo dnf install git`
    (or `sudo yum install git`
    if you have an older version of Fedora or RedHat)

[Here](http://happygitwithr.com/install-git.html) is a another resource.

I do **not** recommend GitHub Desktop. It does not help learn git,
and makes it too easy to "commit" things we don't really mean to.
That caused trouble for several students in this course in the past.

## configure git

run `git config -l` to list the current configuration for git.
Most likely, git doesn't know about your name etc. Set it like this,
but substitute my info with your own info:

```shell
git config --global user.name "Cecile Ane"
git config --global github.user "cecileane"
git config --global user.email "cecile.ane@wisc.edu"
git config --global color.ui true
```

- To be professional, use your actual first name and last name.
  Your commits will be labelled with this user name,
  so make it informative to communicate with collaborators
  (and to show future employers).
- The `github.user` should be your github user name.
- The email above *must* be the email that you used to create your github account,
  to "push" work from your laptop to your own github repositories later.
  If you want github to keep your email address private, then use the
  address below instead, but replace my github user name by yours of course:
  ```shell
  git config --global user.email "cecileane@users.noreply.github.com"
  ```
- The last line is to get colors in the terminal when git will
  show changes (red for deletions, green for modifications).

Then run `git config -l` again to check that your git configuration is good.

One more configuration you should update is the text editor that
git will make you use, when you will write "commit messages"
(one-line summary of your changes in a given snapshot).
The default is "vim". If you never used vim, I recommend that you
change the git text editor to something easier to use,
such as nano or emacs. Do either one of these below, depending
on your preferences:

```shell
git config --global core.editor nano
git config --global core.editor emacs
```

More on git configuration: on
[software carpentry](http://swcarpentry.github.io/git-novice/02-setup/index.html).

## communicate with github

After you get work done on your project locally (on your laptop),
you will want to "push" this work to github. To avoid having to type
your github password over and over, we will use "ssh keys".
The steps below follow the github
[help](https://help.github.com/articles/generating-an-ssh-key/) on ssh keys.
Lots of details on the process [here](http://happygitwithr.com/ssh-keys.html) too.


1. check to see if you already generated a key pair earlier, in your hidden
  directory `.ssh` (recall that `~` is a shortcut for your home directory):

        $ ls -l ~/.ssh
        total 40
        -rw-r--r--  1 ane  staff    72 Mar 24  2018 config
        -rw-------  1 ane  staff  3243 Mar 24  2018 id_rsa
        -rw-r--r--  1 ane  staff   745 Mar 24  2018 id_rsa.pub
        -rw-r--r--  1 ane  staff  6289 Jul 13 09:50 known_hosts

2. if you don't have a folder `~/.ssh/` or
  if you don't see a pair of files like `id_rsa` (private key)
  and `id_rsa.pub` (public key), then you need to generate one.
  To do so, run this, but substitute with your own address of course,
  the same address that you used to create your github account:

        ssh-keygen -t rsa -b 4096 -C "cecile.ane@wisc.edu"

    when prompted, keep the default options and do *not* enter any passphrase
  (just press "enter"). Then make sure your ssh authentication is working and
  that it knows about your new key:

        $ eval "$(ssh-agent -s)"
        Agent pid 12584

    If you have macOS Sierra 10.12.2 or later,
  create a file `~/.ssh/config` if you don't have one, with:
  `touch ~/.ssh/config` then
  open and modify this `~/.ssh/config` file with this:

        Host *
         AddKeysToAgent yes
         UseKeychain yes
         IdentityFile ~/.ssh/id_rsa

    next, run this for Linux users:

        $ ssh-add ~/.ssh/id_rsa

    or add the option `-K` for Mac Users:

        $ ssh-add -K ~/.ssh/id_rsa

3. tell github about your new key:
  run `cat ~/.ssh/id_rsa.pub` to view your public key,
  copy it to your clipboard and paste it into github’s form.
  To get this form: go to github, click on your profile photo (top right corner),
  click "Settings" then "SSH and GPG keys" on the side bar, then
  "New SSH key". Paste your key into the "Key" field. For the title,
  pick a tile that describes your laptop. Each laptop / desktop / server
  that you use will need its own key. Click "Add SSH key" to finish.
  You may need to confirm your github password at the end.

4. finally, check that git, on your laptop, can communicate with github:
  `ssh -T git@github.com`
