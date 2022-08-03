---
title: "Git version control system part-2"
date: 2021-09-09T08:37:00+05:30
draft: true
type: "post"
tags: ["git", "tutorial", "blog"]
---

let's talk about Reverting, Branching, Working with remote servers in today's episode 

## Reverting 
In previous blog we wrote a lame script to understand git and it's workflow , let's continue working with it today
if you've been following along you'll now have a git repository with 2 commits, one with commit message `Added a lame script`
and another with `changed from lame to super lame`. Let's revert back to the original *lame* script since the script we have now actually does some meaningful
work and we don't want that :) .

Let's take a scenario where you mistakenly typed in wrong commit message and commit the changes to git history but you want to change it.
You can do a `git commit --ammend -m<updated comit messge>`


