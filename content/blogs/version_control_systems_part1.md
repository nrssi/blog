---
title: Git version control system 
draft: false
date: 2021-09-04T08:42:25+05:30
type: "post"
tags: ["git","tutorial", "blog"] 
---
## Table of contents 
1. [Version control systems](#vcs)
2. [Git](#git)
3. [How git works](#working)

## Version control systems {#vcs}
Version control systems are software tools which are used to keep track of changes made in a project, over the time softwares have gotten smarter including 
version control systems, modern day version control systems not only provide source control but also provide collaboration of large team without any hassle.

--- 

## Git {#git}
Think of git as that one friend who remembers every mistake you did in you're entire lifetime and plans revenge... Kidding :).
Git is a software that tracks changes in file system, that's all that git does.
**why is it soo popular then?**  
  Well.. it's really good at what it does and puts less strain on the user.  
  it's open-source and completely free.  
  
Before we continue, you should know some terms regarding version control in git.  

***Repository:*** It is simply a directory in which there are files that are tracked by a version control system.  

***Commit:*** Git maintains a timeline in which all the changes are reflected. A commit is simply saving the current changes to that timeline.Each commit is 
identified using a unique ID.  

***Staging:*** Staging is a process of adding files and preparing them for a commit.  

***Unstaging:*** A reverse process of staging, removing already staged files from queue  

***Trunk*** It is also referred as main or master branch.  

***Branching:*** Branching is a process of creating a branch. A branch at the time of it's creation will look exactly the same as trunk, later changes can be made 
to this branch instead of messing with main code base.  

---

## How git works {#working}
People in the tech make it soo boring while explaining git by using really big terms and i'm tired of it so i'm gonna explain things as easily as possible 
(**Note** Logically things work differently in git, I'm using simpler terms to explain them).  
First things first git is a Distributed version control systems which means that each member who works on the project will have his own copy of repository on his 
local machine to which he'll be making changes to.

let's setup our git credentials and create a lame Hello world project.
we need to setup our name and email id by using `git config --global user.name <name>` and `git config --global user.email <email>`. They are required since git
uses them to mention who did certain changes to the project.

first we need to create the project by making a directory. Let's call it *lame* now this lame folder is going to be the place where we do all the stuff so let's
ask git to track all the *lame changes we make here* we use command `git init` to do that, all this command does is start a new git repository.
we'll add a file called **hello.py** and the following code to it.
```python
print("Hello world")
```
but is git tracking this one yet??? let's check by typing `git status` 
```
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```
As you can see in the last line git says there are no changes to commit. Why!!! we created a file and also wrote some *lame* lines to it then why isn't git tracking 
it??? because we didn't tell it to do so... if we run the same command with a `-u` flag it'll show us the untracked files which will include our hello.py.

We can tell git to track certain files by using `git add <filename>` command now let's run `git add hello.py` to tell git to track hello.py 
Now we can check the status again and there it is our lovely and completely *lame* hello world script.
let's commit this to make the change visible on git's timeline by using `git commit -m"Added a lame script"`
```
[master (root-commit) 18bdf1c] Added a lame script
 1 file changed, 1 insertion(+)
 create mode 100644 hello.py
```
Woohooo that's a lot of work there our project is complete but let's change our script to greet a list of people
```python
names = ["Joe", "Candice", "Anakin", "Kenya"]
for name in names:
    print(f"Hello %s" % name)

```
That outputs some neat stuff there ahaa how lame :). Let's stage the changes and commit them,
now our lame script is still lame but lamer (•̀ᴗ•́)و ̑̑ .

to check all the commits we did let's do a `git log` that gives us  
```
commit 628575171a070569d186ffd1562896ea83176223
Author: N R Shyamsundar Iyanger <nrshyamsundariyanger@protonmail.com>
Date:   Fri Sep 3 21:07:39 2021 +0530

    changed from lame to super lame

commit 18bdf1cdb9ed945e9e670bc471800688782567cd
Author: N R Shyamsundar Iyanger <nrshyamsundariyanger@protonmail.com>
Date:   Fri Sep 3 20:57:43 2021 +0530

    Added a lame script
```
As you can see each commit has it's own unique hash, author and his mail. The reason commit messages should be 
descriptive is to identify the changes done in a particular commit so don't go around giving messages like `changed from lame to super lame` instead give `changed from lame to trash` haha kidding.

We'll talk about reverting, branching, working with remote servers in the upcoming blog
