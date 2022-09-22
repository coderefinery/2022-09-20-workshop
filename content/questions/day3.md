+++
template = "page-with-toc.html"
title = "Questions and notes from workshop day 3"
+++

## Icebreakers

### Icebreaker question #1
I want today to be:

- faster: oo
- slower: 
- same as yesterday: oooooooooooooooo
- more exercises: oo
- more type-along: oooo
- more demos while just watching: o
- same as yesterday but slight pauses during type-along: ooooooooo

Any other feedback from yesterday?:
- Some people are just *memorizing commands*, it could be useful to have a overview of the concepts before starting with the commands.
- In type alongs, you could say which keys to push
- I think it is nice to hear your personal experiences of how you Git on a normal day, it gives a good idea of how it is incorporated in your workflow. 
- SSH keys are an issue. The info in the video and in the instructions on GitHub to which link is provided is conflicting. 


### Icebreaker question #2
If you could seamlessly share your work with others (your friends, or anyone in the world), what would you do?
- probably code a bit more clearly
- Stop being so anxious about my work, since there will be many checkings along, many friendly "peer-reviewers"
- Finally writing documentation and using meaningful variable names
- Feel more pressure to make my projects readable and pretty immedieatly
- ^^^ This
- Make apps
- Explain/comment more clearly what I am doing and why. Also ask more feedback.
- Learn more since I can get feedback
- Contribute to larger shared projects 
- Introduce *easter eggs* in my projects :egg:




### Participating in collab exercise via stream-only

(this is not relevant for teams and zoom groups)

Please open an issue here: https://github.com/cr-workshop-exercises/centralized-workflow-exercise/issues

With this we will add you as collaborator to this exercise.


1. Guys, you're talking over each other in the zoom. I guess some of you have the others muted.
   - thanks. i will raise it
   - Now it's fine (y)
   - ok for me
   - thanks for reporting!


2. once we pull some resources from github, which of the previously branches will be downloade? (imagine the source code in github has many branches)
   - If you run `fetch`, it will update the view of all remote branches - the `origin/...` branchs (but won't modify your branches)
   - `pull` = `fetch` + `merge` so I *think* that it would update your current branch, but the `origin/...` branches would change, too.


## git-collaborative
https://coderefinery.github.io/git-collaborative/


### Concepts around collaboration
https://coderefinery.github.io/git-collaborative/remotes/


#### Poll:
Too fast: 
All clear: ooooooo
Confusing: 
Too slow: o


3. No questions because everything's good!
    - Same here +++++
    - My guess is participation dropped a little (?) We are less than half than yesterday in our room.


4. Fork/import. Please can you repeat what is the difference?
    - When talking about cloud repositories: Fork is within a given cloud provider (e.g. GitHub or BitBucket) and import is between them.
    - Fork is also often used for a copy of the repository that you intend to change into a new project (not sure if this was mentioned). For example, LibreOffice is a fork of OpenOffice.
      - +1 the two meanings can be confusing.


5. What is the process to make a remote repository a template? Or command instead of clone?
    - on github: settings, make a template button -> this creates a "generate from template" button


6. Is it common to fork a repository and later (how much later?) propose the changes to be reintegrated to the main repo?
   - Absolutely!
   - Follow up: Why would you fork instead of cloning and branching if you want to contribute?
   - So... "fork" is the Github concept that lets you push to your fork and make a proposal from your fork to the original.  If you clone only, how do you send changes back?  You can't directly modify it without permission.  We will see how this works in the "Distributed" lesson today.
        - Good - so the short answer is permissions.
            - Exactly. If you are working on a repo with colleagues that you already know, you could set it up with the permissions to commit right from the beginning. That said, it can be good to write protect the main branch of the code in order to prevent pushing to main without review within the team.

    
7. When cloning, we only clone one branch to the local computer. Is not possible to clone the whole repository with all commits/branching history?
   - A clone actually does have all branchs and history.
   - Try `git branch -v` to see them - they are `origin/...` branches so "remote tracking branches" - they don't appear as local branches immediately.
     - I think it should be `git branch --all`

8. If I am working on a project and it has some collaborators, do I have to make the project public in github? I would not like to make it public before it finishes. 
   - +1
   - You can leave it private until you are ready to make it public.  This would be a typical workflow (github supports free private repositories now).
   - But if I make it private, how can the others clone it?
   - You can invite other person to have access to the repo. As owner of a repo, you can send an invite to anyone who has an account on Github.
     - Alternative: have one repo that is private and one that is public. On the public one you have the `main` branch. On the private one you have all unpublished branches.

9. Unrelated. Where I can find the definition of the alias `git graph`?
   - https://coderefinery.github.io/git-intro/reference/#commands-we-use
   - `git config --global alias.graph "log --all --graph --decorate --oneline"`


10. Can we get a real life example (for example from one of your repositories) of a pull request after forking? So to see the size of changes.
    - From this morning: https://github.com/coderefinery/git-collaborative/pull/237 (but this is just a pull request for a branch, right? not a fork)
    - They can be large or small: single spelling fix or re-writingbig parts.


11. Can you explain the "origin" concept again?
    - `origin` is the convential term for "the place from where you cloned from".
    - git, by default, when you `git clone`, it a remote with the name `origin` and that name can be used with `git push` and `git pull` to send changes back and forth.


12. If we clone and then push our committed changes will we have to decide if we want to push to the original central repository or to a new central repo that we ourselves create? I'm thinking a fork is always set up to push to a newly created central repo to welcome in comming changes from us. 
    - Yes, you need to make that decision.  Usually it is easy, since you often don't have permission to the original repo.  The "push" (actually more like a "pull") from the fork to the original is within the Github platform.


13. When one is making changes and commiting, how big of a change should be included in a single commit? Is it reasonable to commit all small typo or sort of...aesthetic changes?
    - Good question. In general it is better to commit more often, rather than to seldom. One workflow that I sometimes use is to work in a fork of a repo that I use only for myself, and once the material is ready, I copy by hand the new content to the a branch in the original repo. This can be smooth if the new material is in form of new files, e.g. new source code files or website subpages.
        - Follow-up: is this something we can adapt in the collaborative group or are there still some "gold standards" that should be kept?
            - Each team / project does over time develop some habits. And that would then be the "gold standard" for that project.


14. Why **fork** and not **commit in a different branch** and then request for a merge?
    - In this "Centralized" example, that is what we do.
    - But if you don't have permission to push to the central repo, then when you make your own branch, you can't push it anywhere to make it visible where it can be merged.
    - so this is useful when you are contributing to some project where you don't know the original people


15. Is the `master`/`main` naming dilemma relevant for today's first exercise?
    - Same as yesterday. But the branch can be renamed as you wish.


### Centralized workflow
https://coderefinery.github.io/git-collaborative/centralized/


16. What are other common structures? 
    - We'll see the "distributed" structure in the second exercise.
        - Follow-up: are there any common derivatives of the centalized structure?
            - People can make their own forks anyway, if they don't want to pollute the central repo with their own changes.  Then there can be sub-forks, and so on.  Really, anything is possible (but that makes it hard to teach)


17. For those who requested to be added to a team yesterday, how do we know who is in our group? and how do we decide who the team leader is? I just got a link to 2 repositories (2 "cr-workshop-exercises" )
    - Are you doing this via the stream (requsting access via the cr-workshop-exercise group) -> I applied via this, yes.
    - You are in one giant group with everyone else.  You will see which repositories you can use in the exercise (talking about this now)
      - Thank you!


18. Why does `git diff` not show any staged changes, only unstaged? Can we make it show? Could be useful for deciding commit-message?
    - `git diff --cached` will show staged changes. Or `git diff --staged`, which might be easier to remember!
    - this surprising behavior can be useful as you can use `git diff` to see new changes since staging last. I typically stage several times before committing.

19. Please mention the tasks to be done. By the time I accepted the invite, the tasks were already explained and I missed it.
    - ok will do after break. in short: your goal is to open a pull request, so everything until and including step H
    - Can you give me the link to the page being shown in the stream? ok got it


20. Will all the people be added to the repo after the break?
    - this is stream participants?
    - yes, I mean the stream participants
    - we have hopefully already added everybody who opened an issue at https://github.com/cr-workshop-exercises/centralized-workflow-exercise/issues
    - My issue is still open in the recorder version, I didnt get an email yet
         - ok working on it ...
            - done


21. When we pull a rep on a local machine, should we create a branch of that again? or can we make the changes on the original version we have downloaded?
    - Take note: `pull` is the transfer from remote to local
        - Pull is pulling from Place A to place B in general, it can be from your copy to the original, from a non main branch to main, or pulling online modifications to your local copy.
            - This is not clear. Pull is pulling from A to B. Push is pushing from B to A. But what is A and B? I'd need this to understand how it works 
                - The problem here is that "pull" is pretty universal pulling from somewhere else (you can pull almost to anywhere, or ask for someone to pull your changes - the pull request ). Pushing commonly refers to uploading changes directly to a repository.
                - The terms local vs remote are tricky in the git context, as they always depend on your point of view. But in general `local` refers to the local copy on your machine, `remote` to the online repository your local repository copy is linked (most often, but not necessarily, on your github page) to and `upstream` c
                - ommonly refers to a `remote` repository that a forked repository on your github page is copied from.
                - So in summary: A and B can be any repository when it comes to pull/push. There is not really a restriction on what they can be. BUt the most common scenarios are probably:
                    - Creating a pull request from a forked repository to the source repository (so that a maintainer/owner can then pull from your repo to the source repo)
                    - Pull changes from a remote repository to your local copy
                    - push changes from your local copy to a remote repository
    - That depends a bit. If you clone a fork of a repo (i.e. your copy of the original), you can modify the main branch, submit the changes directly to your copy and open a Pull request on the original repository with your modified main branch, and open pull requests  


:::info
### Break until xx:10 (exercise after the break)
Remember to take your break - we will come back to officially start the exercise time.
:::


::::info
### Exercise Centralized-1, until xx:55
https://coderefinery.github.io/git-collaborative/centralized/#exercise-part-1-creating-a-pull-request

You will try to do that exercise, steps A-H.  The final state should be opening a pull request to whatever repository you are working on (your team repo, or the stream repo).  The general steps:
- Clone (make sure to clone with ssh, not using https otherwise you won't be able to push back)
- Make branch, commit
- Push the branch
- Go to Github web interface and open pull request.

:::danger
Alert!  You should use a SSH url to clone, not the web address.  You can find the SSH url from the green "Code" button on the web page.  For example, `git@github.com:cr-workshop-exercises/centralized-workflow-exercise.git`

If you get a password request when pushing `Username for 'https://github.com':`, you can change to ssh this way (use the right repository-url, recorded one or not):
```
git remote set-url origin git@github.com:cr-workshop-exercises/centralized-workflow-exercise.git
```

:::
I am:
- done: ooooooooooooooo
- need more time: o(11:00 please)
- exercise worked well: ooooooooooo
- had problems: 
- Overcaffeinated: oooo
- undercaffeinated: oo
::::


22. When I try to clone the repositiory I get an error: "remote: Not Found // fatal: repository 'https://github.com/cr-workshop-exercises/' not found"
    - You need to use `https://github.com/cr-workshop-exercises/centralized-workflow-exercise` - your URL is organization, this includes the repository.  There are two options.
    - so in the instructions it says `git clone <repository-url> centralized-workflow-exercise`, so is it the full url and then centralized-workflow-exercise again or that is part of the url?
    - Always the one with two parts (like what I pasted).
    - Ok thanks!
    - wait!  you should clone with an ssh url, found from the repository.  See the alert above.


23. I forgot the -u when pushing. Can I fix this after the fact?
    - It's not a problem - `-u` only says "remember this for next time", you can use it later or be explicit each time.
      - and you can also use this when pushing the second time and it will connect the two then.

24. in the cloned project, in .git/config there is https://github.com/cr-workshop-exercises/centralized-workflow-exercise-recorded.git
    Shouldn't it be some ssh git@github.com:something....  ?
    - that depends on how you cloned it. if you cloned from https, it will use the https address, otherwise it will use the ssh address.
    - Sorry, did not pay attention
    - See above for how to recover (red box under exercises)


25. Sorry. I was in a hurry and commited accidently to the master instead of my branch. What do I do?
    - Following options:
        - 1. create a branch afterwards (it will have your changes from master) and push that one online without pushing your master branch.
        - 2. reset your HEAD on master, to the commit before the new commits, create a new branch from there and then cherry-pick your changes (i.e. remember the commit id and then - on your branch - run `git cherry-pick <commitID>`)   
        - [course materilal- recovering from committing to the wrong branch](https://coderefinery.github.io/git-intro/recovering/#recovering-from-committing-to-the-wrong-branch) 


26. Why is it called a pull request? Am I not requesting to have my branch be merged into the main?
    - You are correct!  "Merge request" would be a more proper name, and that is used by platforms other than Github.
    - Most often you essentially request someone to "pull" your changes (assuming there are no conflicts) i.e. essentially you ask someone to `git pull yourRepo/yourbranch` on the branch you want to be pulled into.  

27. If I as the admin of the repo do a pull to get my local copy up to date after a collaborator has pushed a change, I do not see the changes the collaborator has made? Why is this so? Would it not make sense that I saw this update even though it is not yet merged into main? 
    - You probably can see it if you look around enough.  Does `git branch -a` show an `origin/the-branch-your-collaborator-made` branch?  If not, try `git fetch` first. - Using `git fetch` worked out, Thanks!    
    - So you can see it here, you can `git checkout` that branch to investigate more, merge locally, etc.


28. I use notepad++ for editing my python codes. So, instead of nano (configured with git), if I continue editing with notepad++ and then stage+commit, is it the same? If it is same, then what is the point of configuring an editor (like nano) with git?
    - That works just fine.  We suggest nano only because it's simplest and usually works for everyone (important when teaching this many people).
        - ok thanks
    - Configuring an editor with git is mainly used so that git commands that open an editor call the right one (e.g. some conflict resolution commands open an editor). 


29. Is it possible to directly open the files inside the local repo and modify them using some editors (like notepad) and then save them and stage them in the git bash? (Is it also possible to modify the files somewhere else inside the local machine and then transfer them to the local git repo and stage them?)
    - Yes (and yes, even though I wouldn't recommend this unless you have a good reason)
    - better than transferring between computers by hand is to place it on github/gitlab and then synchronize changes with pull and push

30. Why should we use the SSH and not the direct url? What is the danger?
    - For cloning using https is fine, but if you want to push, git will need to check your identity, and if you use https, you have quite a bit of work setting up the authentication.
    - (you used to be able use username+password with HTTPS url, but that option was removed about a year ago.  SSH is simpler than other options)


31. When cloning a repo, why some branches are included and some are not? How to pull all branches?
    - The branches get renamed from "branch_name" into "origin/branch_name". You can see them using `git branch -v`.
      - I think it should be `git branch --all`

32. Why is the expression 'pull request'? In gitLab it's 'Merge request' which seems much more intuitive (sorry if this has been asked before).
    - see #26
    - Excellent, thanks!


33. In step you showed this: git branch yourname-somefeature master, but know it was like this: yourname/somefeature why?
    - The `-` vs `/` has no special meaning.  We changed the recommendation to `-` because it was less confusing (the `/` in `origin/...` *does* mean something)
       - RB: sorry. When working on my own I use "/" but for presenting I should rather use "-" for less confusion.

34. Can I delete the branch after pushed to remote repo if I don't want to merge it?
    - Yes.  It will stay on the remote until deleted there.


35. The title of the pull requests is practically the same as our commit...if we change the title, it will be different than the commit of our changes. Can this pose a problem?
    - No problem, they can be the same or different.  The pull request title/description isn't stored in the repository history.
    - if the PR (pull request) contains only one commit, it inferst the title from the commit message. you can still change the title. this becomes different if PR contains many commits, there it's good to have a summarizing title


:::info
### Break until xx:25
:::

36. I got this error: 
    ```bash
    ERROR: Permission to cr-workshop-exercises/centralized-workflow-exercise.git denied to user.
    fatal: Could not read from remote repository.
    Please make sure you have the correct access rights
    and the repository exists.
    ```
      - Did you request to be given access (make the issue), and did you accept the invitation you got from it?
      - No, how do I do that?
      - https://coderefinery.github.io/git-collaborative/centralized/#exercise-preparation → Participating via stream → If you have not requested access


37. At some point it would be nice if you could say something about common pitfalls or experiences or maybe best practice when working several people on larger projects, as I go a long in my projects I usually get a clearer picture of functionality and sometimes want to change basic classes or functions made in the beginning of a project, but if other people are developing on the project I suppose this would introduce a lot of conflicts
    - The last part of today is practical ideas of how to contribute, where we discuss some of this.  If we don't remember the this question then, raise it again!
    - The best thing for these kind of situations are tests (imo). As long as the tests succeed, you should be fine in changing the underlying classes. But any time you have to change a test, you are introducing a breaking change, which might not be what you want.
    - and to open an issue first and collect feedback before making a change. the issue can also inform others about the changes that are coming up.

38. How would you manage something like credentials in your code when collaborating and sharing code online? Use a config file ignored using gitignore?
    - Correct.  Then share that config file some other way, or maybe each person has their own credentials in there.  Maybe even a "secrets" git repo that is handled separately.
    - GitHub and GitLab can also store repository secrets without exposing them in the history or test outputs

39. The admin and I (contributor) are sitting next to eachother comparing trees. We have both fetched, but the trees are different. Do we need to use some commands to make the trees align in the future. I have one branch that is not pushed yet.
    - Hm, does `git graph` show any hints (like, are you at slightly different places in the graph)?
    - Do you need to fetch and checkout the current master branch?
        - I will try this.
    - Updating your local copy: https://coderefinery.github.io/git-collaborative/centralized/#step-2b-update-your-local-copy
        - Thank you.


40. After merging PR and deleting the branch in GitHub how to delete the local branch?
    - `git branch -d BRANCHNAME` (it will warn if it's not merged,  `-D` will force)


41. In the repository there is a file `/.github/workflows/test.yml`. What does it do?
    - this is in the forking one. we will comment on that but this will run an automated test on each pull request (in this case it will check whether recipe title contains the word "taco" if I remember correctly; so the test is silly but we wanted to show that this is possible)


42. In the exercise we just did - what exactly is referred to as "fork"/"forking"?
    - In our example, "fork" in a Github concept that means "I want a copy of the repsitory under my user, linked to the other repository"
    - "fork" can also be a generic term for a derivative copy of some code.


43. When I type `git graph` in git bash on my computer, I actually see many branches, not just mine. But if I type `ls`, I only see my file. Why is this? This was before I typed `git pull origin master`.
    - `git graph` is defined with `--all`, which means everything - your branches and all branches on all remotes.
    - We just talked about how to update your local copy with the other changes: the `pull` part.


44. Your radovan/another-pasta is now not updated, right? How could you update this branch? For example, it might happen that someone fixed a bug that you can use on your branch as well, and you want to keep working on your branch.
    - `git fetch` (updates the view), `git checkout radovan/another-pasta` (make sure you are on the branch locally), `git merge origin/radovan/another-pasta` (this brings those changes in to locally)
    - follow-up: so then you have the updates of main, and all your own changes to the branch?
    - It depends on what you merge.  You could merge all main changes into your branch (`git merge origin/main`).  Or you could only merge the changes made on that particular branch (like the changes from code review, `git merge origin/YOUR_BRANCH`)
    - if I wanted to integrate "upstream" changes (changes made by others) into my branch, I would merge master into my branch after updating master. or I would rebase my branch (we did not shown or mentionned how rebases work)
    - Correct.  I would often do rebases if I am the only one working on it, but it's a bit much to teach right now.


### Distributed version control
https://coderefinery.github.io/git-collaborative/distributed/


45. When you fork a repository, will all commits from the original repo be copied (i.e. even those which are e.g. not in the forked master branch)?
    - In general, yes. You can choose to copy the main branch only (in GitHub this is a checkbox in fork page)
        - So if you only do fork master, are the remaining commits in your fork as well, since the git database keeps things even if they are not part of branches)? 
            - Not sure, but I think it only copies the data it needs. In general, git will occationally remove commits that are not in any branch or tag.
    - Commits that are not in any branch are not copied


46. when I fork a repo, how do I get changes made to the original repo, while I am working on my fork version?
    - At the end of this episode we talk about how to update the fork copy.
    - we will show this in the last ten minutes. material also contains 3 routes to do that. the simplest one is: there is a button on your fork called "Sync fork"


47. So the cloning process is the same for forking and as in the previous exercise?
    - Yes, clone is the same.  But you clone from your fork (your username in URL), not the central one.


48. Can I have different origin-like items, that is different pointers to different URLs? One for  cloning from a place and one for fork form another place, for example?
    - Yes, if you have a fork, you might want to add the "upstream" repository to your remotes, which allows you to pull changes from there to your local copy, that you can then push to your fork. But if those two repos are disconnected (i.e. something completely different, you are likely to get into a lot of conflicts). If you want to add a second repo to your repo, you might want to have a look at git submodules.


49. why https won't work?
    - It will work for clone, but not for push later (HTTPS username+password was disabled in Github a few years ago).
    - ok

50. can you create the fork from git bash or does it have to be done in github?
    - There is a Github command line interface that does it, but "fork" like we are talking about is a Github concept so not directly built into git.  https://cli.github.com/

:::info
### Exercise until xx:20
https://coderefinery.github.io/git-collaborative/distributed/#exercise-part-1-creating-a-pull-request
Goal: do this forking process and make a pull request (to a repository that you have no access to).  Steps A-E.
If you can't make it all the way, it's OK (next week does not depend on this, but you can practice more then)

I am:
- done: oooo
- need more time: o
- exercise was good: ooooo
- exercise needs improvement: 
:::


51. how can I change just the commit message of my previous commit?
    - Have you pushed it anywhere yet? no
    - OK, so make sure you haven't done any more `git add`s (otherwise it would be included), then `git commit --amend` and it will let you adjust the message.  It amends the previous commit, you could add new changes or only edit the message.
    - ok, thanks! I tried that, but with -m and a changed commit message, which threw an error. without the -m, it works
    - Strange, `--amend`  with `-m` seems to work for me.  I guess different git versions, anyway, it works.


52. What you do if you clone the froked repo in wrong folder ? i tried removing the directory and it says "rm: forking-workflow-exercise//.git: Permission denied"  etc. i was trying rm -r.
    - I think it makes some files in `.git` not wwriteable.  If using command line, try `rm -rf THE_DIRECTORY` (be careful the directory is right!).  The `-f` changes the permissions so it can be deleted.
    - i tried and it deleted this time. Hope there is no specific way of removing such repos.
    - It's fine to just delete.  All data is there, you probably still have the copy on Github.


53. How do I edit a commit message that I have already commited?
    - `git commit --amend` will open the editor and you can edit it


54. Can you also create a pull request for your own fork without sending it to the central repo?
    - Yes!  Between any two forks (or the same repository).


55. When I am a collaborator in a project, and working on my local computer, what should I do at the end of the day if the work is not ready for commit but I want to have a backup on Github. 
    - The simplest is, make a branch for this work, commit to that branch, and push that branch.


56. I get an error when pushing error: `src refspec <myforked repo>does not match any`
    - exactly what command line are you running?
    - git push origin -u forkkushagra-cw-exercise
    - Is the branch name correct?
    - yes
    - I'm not sure... what is the exact error message?
    - I resolved thanks
    - +1


57. How do I change the commit msg? I staged again and it says nothing to commit.
    - If it is the most recent commit, and you haven't pushed it anywhere, then `git commit --amend` will open the editor and let you edit the message.  (if anything is staged, it will be added to the commit)
        - What if I pushed it already?
        - Then you *can* still modify, and then force push (`git push -f`).  If anyone else has fetched and used this, they wont' get the update and you have chaos.  If it's your private branch no one else is working on, it is OK.
        - Great! it works. thanks


58. Unrelated. What are the URLs of the "HackMDs" of day 1 and 2?
    - Earlier days on website: https://coderefinery.github.io/2022-09-20-workshop/questions/


## Feedback, day 3

Today was:
- too fast: ooooo 
- too slow: oooo
- just right: oooooooooooooooooo
- useful: oooooooooo
- not that useful: 
- will help my work: ooooooooooooooooooo
- will recommend to others: oooooooooo
- needs improvement to recommend to others: o

One good thing about today:
- The groups on Zoom worked very well. +4
- Exercises were very useful. +3
- First time I worked with forks. Very cool:smiley: +1
- We get to develop very useful skills. Just to have seen the interface and get the concepts makes you less afraid to try it out.
- I started feeling confident about using git and github +1
- Review of the pull request included many insights which were very useful.
- veru useful 'material'
- I've been using github to download programs and code but I've never understood anything about it. Now I understand it :smiley:

One thing that should be improved for next time:
- The first exercise could be done in less time (+10)
- The other exercises needed more time. +2
- The explaination of how to download the first repository could be more detailed in the written instructions (what link to use, the ssh version)
    - Thanks, yes, we need to improve that.
- The new teacher should do more linear explanations instead of moving back and forwad. It was difficult to follow for me. Also stop interrupting the other teacher and commenting everything he does. Not my teaching style.
- Have more time for excercises.
- Describing irrelevant commands when explaining another concepts can make it confusing (do I need `git remote --verbose` to set everything up? was it different from `git remote -v`?)
- Examples about undoing changes done to the wrong branch should be discussed more actively. To me, this is the trickiest part of git. (+2, agreed - this is also the thing which makes me scared to test things and practice by myself)
    - Yeah, all of these "changing history" things are hard.  Unfortunately we don't have much time but maybe we could give a dedicated lecture on it sometime?
- As an administrator and learner it would have been helpful if the excercise leader was a bit more clear about the next step so I as administrator didnt have to jump between administrating and reading steps in instructions.
    - I agree, we should work on those instructions a bit more!
- We need more cat cameos :smiley_cat: +10003
    - come back next week!  I will be teaching more then.
- Perhaps the instructor should explain the key content thinking more of the camera than of the screen. (A little bit more lecture-like)
- Can hackmd page be structured or color-coded. There were many ssh related issues today. Going through all to see deeper questions and answers gets difficult.
    - Good question.  I think we are limited in what to do, but in general I would recommend looking only at the bottom, add a new question rather than try to find info above.  we will point you to the answer if it is already there.


Comments on the course format:
- The exercises were much more useful than the very lengthy explanations on the stream. It would have been great to have more time for exercises (eg for reviewing pull requests, trying out stuff) and less time on twitch. +3
- Is there a cheat sheet for the git commands we have gone through up till now? It could be very useful to have one when we have several browsers open and it's hard to find the place where the  command is mentioned. +2
  - Each lesson has a "quick reference" guide that lists most of the commands we use.  If you see commands missing, let us know!  (you can open an issue, see link at top, or make a pull request...)  There is also some extremely detailed PDF cheatsheet I made a while ago. +1
- Exercises are really key becuase it is such a low-consequence way to try out commands. they have made me a lot more comfortable with trying out git commands I am not super sure about
- I would like to have a session dedicated to how to use github as a backup for someone that programmes mostly alone.
    - Yesterday we had an episode that was almost that "Sharing repositories online"
- Click alongs are more difficult to follow than write alongs.
- It would be good if whoever leads the session makes the practical calls on what to do - you have a tendency to discuss the format a lot, also small things that do not make much difference like break now or in 5 minutes. I think the course is great, just power on :)
- Suggestion: in the 1st exercise, you have asked to review pull requests at the beginning of this explanation, my group has done the reviews already. Please indicate more clearly when to do things and when to wait. maybe you could add it  to the instructions for EL to explain what will happen in the stream and how to follow along (review eahc others' requests using different functionalities).
- Suggestion: Maybe there should be some instructions for EL and all those joining Zoom not to open the mic and to go directly to breakout rooms. Otherwise it is quite disturbing ( twitch and zoom audio at the same time). In the previous edition there was no-one in the main room, evrybody went to the breakout rooms directly and it worked smoothly. no (audio) messages needed (but still, amazing organization! weel done)


Other comments:
- All hail Radovan! I think he's an awesome teacher. Talks slowly, clear walk throughs, explains use cases. +3
- Very cute cat +1
- Hopefully more next week!
- Thanks to all the teachers and organisers!
