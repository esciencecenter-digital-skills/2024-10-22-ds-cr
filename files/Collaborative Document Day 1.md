![](https://i.imgur.com/iywjz8s.png)


# Collaborative Document Day 1

2024-10-22 Collaborative version control with git and GitHub 2024-10-22-ds-cr

Welcome to The Workshop Collaborative Document.

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.

----------------------------------------------------------------------------

This is the Document for today:
https://edu.nl/y8rc9

Day 2: https://edu.nl/yebdm


##  🫱🏽‍🫲🏻 Code of Conduct

Participants are expected to follow these guidelines:
* Use welcoming and inclusive language.
* Be respectful of different viewpoints and experiences.
* Gracefully accept constructive criticism.
* Focus on what is best for the community.
* Show courtesy and respect towards other community members.
 
 For more details, see [here](https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html).

Want to report a Code of Conduct incident and you prefer to do it anonymously? You can do it [here](https://goo.gl/forms/KoUfO53Za3apOuOK2).
=### Paper Writing

- Imagine you drafted an excellent paragraph for a paper you are writing, but later ruin
it. How would you retrieve the *excellent* version of your conclusion? Is it even possible?

- Imagine you have 5 co-authors. How would you manage the changes and comments
they make to your paper?  If you use LibreOffice Writer or Microsoft Word, what happens if you accept changes made using the `Track Changes` option? Do you have a history of those changes?

### Schedule

09:30	Welcome and icebreaker
09:45	Workshop Introduction
10:00	Version control with Git
10:30	Coffee break
10:45	Version control with Git
11:30	Coffee break
11:45	Version control with Git
12:30	Lunch Break
13:30	Collaboration with Git and GitHub
14:15	Coffee break
14:30	Collaboration with Git and GitHub
15:15	Coffee break
15:30	Collaboration with Git and GitHub
16:15	Wrap-up
16:30	END

### Places to Create Git Repositories

Along with tracking information about planets (the project we have already created),
Dracula would also like to track information about moons.
Despite Wolfman's concerns, Dracula creates a `moons` project inside his `planets`
project with the following sequence of commands:

```bash
$ cd ~/Desktop   # return to Desktop directory
$ cd planets     # go into planetse directory, which is already a Git repository
$ ls -a          # ensure the .git subdirectory is still present in the planets directory
$ mkdir moons    # make a subdirectory planets/moons
$ cd moons       # go into moons subdirectory
$ git init       # make the moons subdirectory a Git repository
$ ls -a          # ensure the .git subdirectory is present indicating we have created a new Git repository
```

Is the `git init` command, run inside the `moons` subdirectory, required for
tracking files stored in the `moons` subdirectory?

### Choosing a Commit Message

Which of the following commit messages would be most appropriate for the
last commit made to `mars.txt`?

1. "Changes"
2. "Added line 'But the Mummy will appreciate the lack of humidity' to mars.txt"
3. "Discuss effects of Mars' climate on the Mummy"

### Committing Changes to Git

Which command(s) below would save the changes of `myfile.txt`
to my local Git repository?

1. 
```bash
$ git commit -m "my recent changes"
```
2.
```bash
$ git init myfile.txt
$ git commit -m "my recent changes"
```
3.
```bash
$ git add myfile.txt
$ git commit -m "my recent changes"
```
4.
```bash
$ git commit -m myfile.txt "my recent changes"
```

### Recovering Older Versions of a File

Jennifer has made changes to the Python script that she has been working on for weeks, and the modifications she made this morning "broke" the script and it no longer runs. She has spent \~ 1hr trying to fix it, with no luck...

Luckily, she has been keeping track of her project's versions using Git! 
Which commands below will let her recover the last committed version of her Python script called
`data_cruncher.py`?

1. `$ git restore`

2. `$ git restore data_cruncher.py`

3. `$ git restore -s HEAD~1 data_cruncher.py`

4. `$ git restore -s <unique ID of last commit> data_cruncher.py`

5. Both 2 and 4

### Understanding Workflow and History

What is the output of the last command in

```bash
$ cd planets
$ echo "Venus is beautiful and full of love" > venus.txt
$ git add venus.txt
$ echo "Venus is too hot to be suitable as a base" >> venus.txt
$ git commit -m "Comment on Venus as an unsuitable base"
$ git restore venus.txt
$ cat venus.txt #this will print the contents of venus.txt to the screen
```

1. 
```output
Venus is too hot to be suitable as a base
```
2.
```output
Venus is beautiful and full of love
```
3. 
```output
Venus is beautiful and full of love
Venus is too hot to be suitable as a base
```
4.
```output
Error because you have changed venus.txt without committing the changes
```

### Ignoring Nested Files

Given a directory structure that looks like:

```bash
results/data
results/plots
```

How would you ignore only `results/plots` and not `results/data`?

### Exercise: Working as a project collaborator (in pairs):
- PERSON A: Create an issue in the repository
- PERSON B: Clone this repository to your system
- PERSON B: Create a new branch
- PERSON B: Make the changes requested in the issue
- PERSON B: Push the changes to the remote repository on GitHub
- PERSON B: Submit a Pull Request, refer to the issue (e.g. "Closes #1")
- PERSON A: Review the Pull Request
- PERSON B: Address the comments
- PERSON A: Approve the Pull Request
- PERSON B: Merge the Pull Request

## 🧠 Collaborative Notes

### 1. Good Practices in Software Engineering 

#### Programming vs Software engineer

![](https://codimd.carpentries.org/uploads/upload_9cf8e6fe5773a928a6a4eb5d95789be7.png)

- Software engineering is programming integrated over time!
- The use of software engineering best practices (despite an initial overhead) makes your project speed up over time
- Examples of best practices are:
    - version control
    - modular code
    - documentation
    - code reviews
    - automate testing
- These good practices are investiments that make your code development more efficient, reproducible, reusable, faster to debug with fewer errors.
- Good practices are there to help you but do not overdo it; this depends on the type, duration, and how many collaborators you have in your project.
- So, good practices are investments!

### 2. Introduction to Git
#### Why version control?

![Why version control](https://phdcomics.com/comics/archive/phd101212s.gif)

- Version control is a structured way of managing different version of your project.
- Version control is an unlimited undo.
- Version control also allows many people to work in parallel.
- In Git, every change made can be saved (and recorded in the history of your project!) and is referred to as a `commit`

#### The Holy Realms of Git
- `Workspace`: the files you see.
- `Staging area`: add changes to this area; the files wait patiently to be commited.
- `Local repository`: Contains branches, commits, history, etc.
- All this info are gathered in a `.git/` folder.

#### Setting up Git
Check if you have git installed:
```bash
git --version
```
Basic git user settings:
```bash
git config --global user.name "My Name"
```
```bash
git config --global user.email "me@example.com"
```
Set the name of you main branch as ``main``
```bash
git config --global init.defaultBranch main
```
Check git global configs:
```bash
git config --global --list
```
Set `nano` as your default editor:
```bash
git config --global core.editor "nano -w"
```
Check you default git global settings with your editor
```bash
git config --global --edit
```

#### Version control in practice
Go to your desktop:
```bash
cd ~/Desktop
```
Make a new directory:
```bash
mkdir planets
```
Go to that directory:
```bash
cd planets
```
To check where you are:
```bash
pwd # e.g., /home/john/Desktop/planet
```
Initialise a new git project:
```bash
git init
```
Check the contents of your directory:
```bash
ls
```
List also "hidden" folders like `.git`:
```bash
ls -a
```
Check the status of your git repo:
```bash
git status
```
Make a subdirectory named `moons` and go inside it:
```bash
mkdir moons
cd moons
```
In case you have initiated a git inside `moons` and want to not do so:
```bash
rm -rf .git
```
Go back to the `planets` directory:
```bash
cd ..
```
Use `nano` to create a file
```bash
nano mars.txt
```
Enter the following text:
```
Cold and dry, but everything is my favorite color
```
See if the text was written to the file correctly:
```bash
cat mars.txt
```
Check that you have one untracked file:
```bash
git status
```
Track the untracked file:
```bash
git add mars.txt
```
Commit the `mars.txt` file:
```bash
git commit -m "Start notes on Mars as a base"
```
Check that you have committed the file correctly:
```bash
git status
```
Check the details of your commits:
```bash
git log
```
this also give you unique identifiers and details of each commit made.
``` bash
ls -a
```
We will make more changes:
```bash
nano mars.txt
```
Add the following line
```
The two moons may be a problem for Wolfman.
```
Show the changes between the previously committed `mars.txt` file and the current one (not committed yet):
```bash
git diff
```
Edit the file again:
```bash
nano mars.txt
```
Add one more line
```
But the Mummy will appreciate the lack of humidity
```
Add the file to the staging area:
```bash
git add mars.txt
```
Check the difference between the previusly committed file and the newly committed `mars.txt`
```bash
git diff --staged
```
Now commit the changes:
```bash
git commit -m "add concerns regarding mummy"
```
Check that everything is OK:
```bash
git status
```
Check the details of your commits:
```bash
git log
```

#### Exploring git history

Check the difference between the file and the most recent commit:
```bash
git diff HEAD mars.txt
```
Compare with the second to last commit:
```bash
git diff HEAD~1 mars.txt
```
```bash
git diff HEAD~2 mars.txt
```
``git show`` as an alternative to ``git diff``:
```bash
git show HEAD~1 mars.txt
```
```bash
git diff $commit_hash mars.txt
```
Undo changes:
```bash
git restore mars.txt
```
Restore a file using a commit hash:
```bash
git restore -s $commit_hash 
```

#### Ignoring files
Make a directory called `output` and create some files
```bash
mkdir output
touch output/out.csv output/out2.csv
```
To ignore and do not track these files
```bash
nano .gitignore
```
add to `.gitignore`: 
```bash
*.csv
output
```
This will ignore the changes of the `output` folder and any `log.*` file
Add `.gitignore` file to our repo
```bash
git add .gitignore
git commit -m "Added .gitignore"
```

### 3. Collaboration with git and Github

#### Create a new repository on github
1. Open a browser and navigate to github.com.
2. In the top right corner, click the "+" and then "New repository".
3. Give your repository a name (it is common practice to give it the same name as your folder, but this is not mandatory).
4. Make it Public and completely empty.

#### Populating the repository
GitHub will show you 3 options of how to populate the repository:
![](https://codimd.carpentries.org/uploads/upload_9908b762142cebb1de9924d597b187e0.png)

We will use the second option (push an existing repository from the command line).
To push your existing local repo to remote, do:
```bash
git remote add origin git@github.com:$USER/planets.git
git remote -v
git push origin main
```
This connects your local repository to the repository on github.com

#### Working as a project collaborator - typical workflow:
1. Add people as your collaborators so that they can work together with you in our project.
2. In case you need them to take care of some changes/issues, create an `issue` in GitHub and assign a specific collaborator to work on it. 
3. Your collaborator should first make a new branch before anything, and them start working on this new feature.
4. Once changes are done, your collaborator will `push` them into the GitHub remote repository and then create a `pull request` describing all details of the changes made. He/she will also associate this `pull request` with the `issue #` you previously generated.
6. You will then `review` the `pull request`. You can suggest further changes, make comments, give feedback, etc. If everything is OK, you will then `merge` this branch into the `main` working branch.

**remember**: it is considered a bad practice to any push changes directly into the `main` branch.

To update your local repo with any changes made in the remote repository, use:
```bash
git pull
```
This command is exactly the oposite of `git push` we saw before.

#### Working as an external contributor - typical workflow:
- Remove your group member(s) as collaborators from your repository
- Fork another group members repo (Repository page, top right corner)
- Create an issue on the original repository
- Clone your forked repo to your computer
- Make some changes, use a somewhat real-world example so it makes sense to review it (but don't overdo it).
- Push it to your fork
- Make a pull request from your fork to the main repository mentioning the issue
- Consider turning your Pull Request into a draft Pull Request.
- Let your code be reviewed by tagging the repo owner using (@Username)
- At the same time review Pull Request using comments on individual lines. Try to act as if it was a real peer review as much as possible.
- Accept or reject the Pull Request
- (Optionally) learn about merge conflicts and try it out in your collaboration.

#### Resolving merge conflicts locally
Within your `planets` repo, we create two branches, say, `branch-A` and `branch-B`, where the same line of `mars.txt` has been modified. Both of them were originally created from the `main` branch.

Now, we want to manually merge `branch-B` into `branch-A` and solve any merge conflicts locally.

First, make sure you are in the `branch-A`:
```bash
git status
```
If not, do:
```bash
git switch branch-A
```
Then, let's look at the more detailed info given by the `git log` command:
```bash
git log --oneline --graph --all
```

To make the merge manually, do:
```bash
git merge branch-B
```
solve any possible conflicts using `nano` or `vscode`. Finally, we just need to add and commit the changes:
```bash
git add mars.txt
git commit
```

## :ear: Feedback (Morning)
### What went well?
* love the regular breaks +2
* well structured +1
* well paced
* nice overview of basics of git with terminal
* post-it system is great, will steal that idea for my next class :)
* helful stops to make sure everybody is on track
* well-organized +1
The pace is working well for me, nice that we have enough people hel🔐ping around and the regular breaks help to keep concentrated. The general non-expert language also helps understanding better the concepts.
### What can be improved?

* for me the pace is rather slow+1
* the topics are a bit basic 
* temperature is cold +1
* set-up instructions sent previously are not clear about SSH requirement for Windows users
## :ear: Feedback (Afternoon)
### What went well?
* Practice and teamwork.
* I liked the team excercise to practice at our own pace and again I found that the ratio of instructors/students to provide individual help was good.
* All went well
* Good support during exercises
* Nice to have optional excercise
* Nice to see real-world practices of working together using git. 
### What can be improved?
* overview of command used would have been helpful (e.g. to create branch and switch to branch) +4 DONE
* Make exercise a bit different from what was shown as an example at the beginning of the afternoon
* You can add an optional more advanced exercise for the ones that finish early
* The merge conflict bit was nice- maybe include this in the "main" exercise? +1
* Pacing in morning was too slow, but in the afternoon it was a bit too fast (esp. at end on merging). The discrepancy could be addressed. +1
* Live coding and showing is great, sometimes the screen switched a bit too fast to the next step for me. E.g. when you were clicking around on github.com, I missed which tab you were exactly using. This was resolved later but a little confusing. Perhaps nice to sometimes pause a second longer or explicitly mention some basic things. (This is a very minor issue though.) +1

## 💬 Post-workshop survey


## ❓ Questions
* How to resolve differences in your local and remote repository when pulling?
    * Advice 1: try to avoid this as much as possible in the first place! :) Always `git pull` before writing new commits or creating a new branch
    * If it has happened, you can try to `git pull --rebase`: This will:
        * temporarily move aside the commits you've made locally since local and remote diverged
        * pull from remote to bring you up to date
        * and finally will try to re-apply your local commits **on top** of what you pulled from remote
    
      Note: you may still end up with a merge conflict per commit you've made locally.
    * Alternatively you can specifically `git fetch` to download the remote updates in the background, and then `git merge origin/<branch>` to create a merge commit. This will only create a single merge conflict, that may be harder to solve.
* How do I collaborate with people not so familiar with git? (I’m supposed coding expert at my department, and need to support researchers not familiar with Git or even coding, but help them writing code.)
    * Depends on what you try to achieve? As RSE's working in slightly longer projects, we would probably try to teach enough basics to whom we collaborate with.
    * At least, you could encourage them to use the direct upload feature of GitHub/GitLab to make commits: that way you are still making use of version control, even if you miss out on the features like branching.
* What is best practice if you work with multiple people on same issue? e.g. work in same branch and relay-race pushing or working 1 branch per person “personname-issuename”.
    * In general, we would advise trying to split up the issue into smaller issues so everyone can work on their own feature that can be merged independently.
    * We are also a fan of pair-programming: sitting together to work on something on a single computer
    * If that's not possible, you can also do the relay-race approach, if you know/agree that different people are available to work on it at different times
* How can we remove unnecessary commit changes?
     - undo the last commit but keep changes unstaged
     `git reset HEAD~1`
     - undo the last commit and discard changes (danger!)
    `git reset --hard HEAD~1`
    -  interactive rebase, e.g. last 5 commits = rewrite history
    `git rebase -i HEAD~5`
    - revert specific commit = do not rewrite history, but create an explicit new commit to undo a previous one
    `git revert commit_hash`

* How can we delete the extra branch we created?
`git branch -d branch_name`
Or if the branch has unmerged change
`git branch -D branch_name`

* In practice, do you recommend using the command line instead of e.g. Github Desktop?
    * Use whatever tool you enjoy working with most. We teach the basics via command line, because that is the most basic way of interacting with `git` that is most widely available and guaranteed to have all features available. Everything else builds on top of the CLI (command line interface) tool in the end.


## 📚 Resources
* Upcoming workshops: https://www.esciencecenter.nl/events/?f=workshops
* Schedule of all workshops in the year: https://www.esciencecenter.nl/digital-skills/ (scroll down)
* Subscribe to our newsletter (stay updated on upcoming workshops): eepurl.com/dtjzwP
* Slides: https://esciencecenter-digital-skills.github.io/digital-skills-slides/
* Really nice git book: https://git-scm.com/book/en/v2
* Git cheat sheet: https://education.github.com/git-cheat-sheet-education.pdf
* The Utopic Git History: https://blog.esciencecenter.nl/the-utopic-git-history-d44b81c09593
* Bash git prompt: https://github.com/magicmonty/bash-git-prompt


