# PaperTemplate
A "fork-able" template for writing a paper via LaTeX

## How to Use this Repo to Write a Paper



## Storing Data

Every paper has raw data associated with it.
It is a good practice to store the raw data alongside the paper in a data/ directory.
Unfortunately, git isn't a very useful tool for storing data.
Every time you commit a replace a data file with a new one, it makes a copy, and this can end up generating huge repositories.
This is bad, because it then takes forever to clone, commit, push and pull from repos, and we end up having to pay GitHub to store our data.
We definitely don't want to do this, since we typically generate GBs (and sometimes TBs) of data!
To avoid this, follow this rule: **Do not store your raw data in a directory that is tracked via git**.

To help you keep this rule, I have set up a "data/" directory inside the paper template repository, but its contents are not included when you commit or push your repository.
This is done via the .gitignore file inside the repository's main directory.
This ensures that you can store your data locally along with your paper, but keep it out of the git repository.

However, you still probably want your data to be backed up and shared with others.
To facilitate this, I have added a "hook" that runs every time you push your commits back to the repo.
The hook is a bash script that syncs your data directory to the CAEDM ssh server.
This way your data stays backed up, and you can easily access it anytime you need to.
Additionally, others in the group who are working on the paper should have access to your data and vice versa.
Anytime you clone or pull from the repo, you can also sync your local data folder with the CAEDM server to your local machine.

### Setting up Data Storage
* Set up ssh keys to the CAEDM ssh server
* Make sure you have access to the "softmatter" CAEDM group

### Pushing your data to CAEDM SSH
Notes: 
* This copies data from your local machine to the CAEDM server.
If the files are large, this can take a long time.  
* Because the files in data are not part of the repo (i.e. they are ignored via .gitignore), 
updating these files will change the repo.
In other words, you will not see a change to the git status when you change files inside data.

* Automatically: make a commit and then run a git push. (*Only works when you have changes to the other files in the repository.*)
* Manually: run sh/syncdata.sh from the main directory of the repository. (*Works anytime.*)

### Getting your data from CAEDM SSH
Notes: 
* This copies data from your local machine to the CAEDM server.
If the files are large, this can take a long time.  
* Retrieving data from the external server can only be done manually.
This is to avoid possibly long retrival times the first time you clone the repo.

* Manually: run sh/getdata.sh from the main directory of the repository.

