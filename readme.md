This information is for the UW-Madison course Stat 679:
[Computing tools for data analytics](http://cecileane.github.io/computingtools)

- instructions to [get homework](#instructions-to-get-homework-data)
- instructions to [submit homework](#submit-your-assignment)
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
  To check: do first

        git status

    This should return an error saying that you
  are not in a git repository. If you get this error, great.
  You can safely clone your assignment repository here.
  Create your local version of your assignment repository:

        git clone git@github.com:xxx/yyy.git

    but paste the link that you copied in step 2.

4. navigate (`cd`) inside the new directory, which should be named with the name
  given in step 1 (like `yyy`). Once there,
  you can start your homework. For examples, you should
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
  run `git commit -m "commit message here"`

   example: you created a directory `scripts/` in which you created a file
   `normalizeFileNames.sh`; you also modified the file `readme.md` that was
   already existing (and already tracked by git). Do this to commit
   your new file and your changes:

   ```bash
   git status # gives useful info: read it!
   git add scripts/normalizeFileNames.sh
   git add readme.md
   git status # read! you should see that your work is ready to be committed
   git commit -m "doc in readme, and script to normalize file names"
   git show   # just to check your latest commit. "q" to quit
   ```
- run `git status` to double check: should be all clean
- push the new commit(s) to your github repo:
  run `git push`
- go online to visit your repo on github, refresh the browser and make sure
  it's all good: click on the files, on the last commit,
  check that your markdown syntax is correct and renders
  as you wanted.
- After these steps, your work will be visible to the instructor and TA.
  Make 100% sure that it looks like what you want to be is, because
  that is what you will be graded on: check that all files are there,
  that there are no unwanted files, and check that your readme file
  looks good (with correct markdown syntax).
- After you are 100% happy with your work on github, you may want to
  **tag** your git repository. For example, use tag `v1.1` for homework 1.1.
  To create a tag "v1.1", for example, do this:

      git tag v1.1

    Next, push your tag(s) to your github repository:

      git push origin --tags

    Finally, go to your github repository online and check that your tag
  appears there: click on the box saying "Branch:master" then "Tags".

Now that your work is on github and is viewable to be graded,
you need to submit it, that is,
inform the instructor and TA that it's ready to be graded.
To submit your work, open a github issue in which you write
a description and a link to the latest commit:

- go to the repository that has your work
  (not the repository that contain these instructions!!)
- find the SHA of your latest commit.
  On github, above the file list, look for latest commit SHA:
  it looks like 7 numbers/letters and it links to the commit itself
  (showing the list of changes).
  Right-click to copy the link to this last commit with its SHA. For example, it might
  look like this:
  `https://github.com/UWMadison-computingtools-2018/xxx/commit/0962e0575d`
  You can also get the SHA from the shell: `git log`,
  then copy first 7 or so characters of the commit SHA.
- on github, click on "Issues", then "New Issue". Name your issue like this:
  "Mark homework xxx of firstname lastname", where xxx is 1.1, 2, etc.
  Please indicate your real first and last name, as I might have trouble guessing
  your real name from your github name.
- issue description:
  * paste the revision SHA (link from first step)
  * include comments to help me understand what you did
  * use markdown syntax (this is very important: see grading rubric)
  * click on "preview" to preview your issue (check the link and markdown syntax)
- click "submit new issue".

We will check your work online, read your documentation,
run your code to make sure it works,
then provide feedback on the "issue" if needed,
and close the issue when it's all done.

### group assignments

tutorial [video](https://education.github.community/t/video-group-assignments/3614)
on GitHub Classroom for group assignments.

## get help on your work

You may also open an issue to get help. In this case, do as above but
choose a different name for your issue. Tag the TA and/or instructors,
otherwise they may not be notified.

For group assignments, you can use github issues to communicate with your
group members. This is a great way to get help from / discuss roadblocks with
someone else in your group. This is used heavily in the workplace.
