This information is for the UW-Madison course Stat 679:
[Computing tools for data analytics](http://cecileane.github.io/computingtools)

- instructions to [get and submit homework](#instructions-to-get-homework-data)
- general grading [rubric](rubric.md)
- mark template: download [.csv](marktemplate.csv) template

---

## instructions to get homework data

Each homework assignment corresponds to a github repository.
You must have a GitHub account.
For each assignment, you will receive an email with an invitation link,
inviting you to access the assignment. When you do so,
a new repository will be created, unique to you (for an individual
assignment) or unique to your group (for a group assignment).
This repository will contain the questions and data.
Only you, your group members (for group assignments) and the instructor/TA
will have access to it.

### install git

First, install and configure [git](git.md) on your local machine.

Online: add your real name to your github profile,
to make sure I know who you are!
Please also add a picture of you.

### get the assignment on your laptop

Second, get the content of your assignment repository onto your local machine,
clone it with a `git clone` command, as explained below.

1. go online to GitHub, to the repository that was created for you when
you accepted the assignment invitation.


2. click the green button "Clone or download",
  then click "Use SSH" on the right if you see "Clone with HTTPS" instead
  of "Clone with SSH". Copy the string (or click the "copy" button).
  The link should look like this:
  `git@github.com:xxx/yyy.git`

3. on your laptop, nagivate to where you want your work for this assignment to be.
**This should be outside of any git repository**:
never nest one git repository within another.
To check: do `git status` first. This should return an error saying that you
are not in a git repository. If you get this error, great.
You can safely clone your assignment repository here.
Create your local version of your assignment repository:
`git clone git@github.com:xxx/yyy.git`
but paste the link that you copied in step 2.

4. move (`mv`) inside the new directory, which should be named with the name
  given in step 1 (like `yyy`). Once there,
  edit your readme file to explain what you intend to put in this directory
  and what subdirectories will be there.

5. check that your local repository knows about the remote repository on github:
  `git remote -v`. You should see an output like this:

        origin	git@github.com:xxx/yyy.git (fetch)
        origin	git@github.com:xxx/yyy.git (push)

6. save your work for your assignment in this directory, organized with subdirectories
  to separate the data from your scripts, results etc.
  Instructions to "push" your work and to submit it are below.

### submit your assignment

These steps are to broadcast your work to github, to submit it there.

- save all your homework files locally
- commit the files that you want to submit:
  run `git add filename` for every new file `filename` that you created.
  run `git commit -m"commit message here"`
- run `git status` to double check
- push the new commit(s) to your github repo:
  run `git push`
- go online to visit your repo on github, refresh the browser and make sure
  it's all good: click on the files, on the last commit,
  visit the network page (in "Graphs", then hover on the dots)

After these steps, your work will be visible to the instructor and TA.

To submit your work: open an issue, link to the latest commit, and tag me and the TA (@coraallencoleman):

- find the SHA of the latest commit.
  On github, above the file list, look for "latest commit" followed by 7 numbers/letters.
  Right-click to copy the link to this last commit with its SHA. For example, it might
  look like this:
  `https://github.com/UWMadison-computingtools-2018/xxx/commit/0962e0575d`
  You can also get the SHA from the shell: `git log`, but the first option gives the
  full link to that particular commit on the github repository.
- on github, click on "Issues", then "New Issue". Name your issue
  "Mark homework xxx, exercise yyy of firstname-lastname", where xxx and yyy are 1, 2, etc.
  Please indicate your real first and last name, as I might have trouble guessing
  your real name from your github name.
- issue description:
  * tag me and the TA by including the text `@cecileane` and
    `@coraallencoleman` anywhere in the message
  * paste the revision SHA (link from first step)
  * include comments to help me understand what you did
  * use markdown syntax (this is very important: see grading rubric)
  * click on "preview" to preview your issue (check the link and markdown syntax)
- submit "new issue". I will receive an email automatically because you tagged me.

I will check your work online,
will run your code to make sure it works,
then provide feedback on the "issue" if needed,
and close the issue when it's all done.

### group assignments

tutorial [video](https://education.github.community/t/video-group-assignments/3614)
on GitHub Classroom for group assignments.

## get help on your work

You may also open an issue to get help. In this case, do as above but
choose a different name for your issue.

If I do not reply fast enough, I suggest that you share your repo with
the class (github user: "UWMadison-computingtools-2018") and that you tag
someone else from the class, to get help from / discuss your issue with
someone else. Then use the github issue feature for your discussion.
Your goal is to learn these computing tools, so make sure you do the work
yourself, even if you ask for help from someone else.
