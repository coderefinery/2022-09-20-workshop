+++
template = "page-with-toc.html"
title = "Questions and notes from workshop day 2"
+++

## Icebreakers


### Icebreaker question #1
I am watching:

- by myself:  oooooooooooooooooooooooooooooooo
- in a small group: oooooooooo
- in an organized group: ooooooooo
- group is online: ooo
- group is in-person: oooooooooooooo


### Icebreaker question #2
What has been your most collaborative project so far? (tech or not) How many people and how did you work? Do not put names or identifying information on this page:
- In the old good days, you met in the office...
- Unfortunately less collaborative work than I wished. Mostly only ever had one collaborator but mostly worked on quite different chunks of code using SVN. Learned so much about principles of version control though. But looking forward to doing more in my new job-group!
- a group project for a master course. We were 3 people and split the tasks. Common parts were difficult to merge.
- Not technical: international public opinion poll - around 200 people involved, including interviewers and translators. The communication was done through email, there were some specific software for translators and a share drive to drop the data/deliverables. Interviewers provided their comments in the surveying tool.
- a group project for a master course. 17 people. Split into several smaller groups to design an infrastructure project. Several meetings with good structure were needed and it worked very well. 
- writing a manuscript, 6 people, overleaf.
- I worked with fit for my Master project with my supervisors existing code, the purpose was to include new code in existing one and also be able to take help from him.
- A fieldwork project with 8 other students, we worked on a shared server
- working on code with my supervisor which we send back and forth zipped via mail :see_no_evil: and worked on manuscripts in overleaf with several people
- 6-month long project in a group of 4. Shared documents on google drive
- 2 people project in overleaf
- 1.5 years 6 people research and code base development
- 3 to 5 people working in some software to identify weed in agricultural setups. Used a private git server.
- it's the project I am currently working on. I am working with an ice sheet model that I want the community to use, so making it easily accessable and documented is crucial
- for a paper, in a rather large group of 10 authors
- modifying a user guide documentation contributed by several people. Github was used for this.
- 6 people for a course project. Used GitLab to share code and MS Teams to collaborate on documents.
- large industry projects with many people. Did not use git, but onedrive for text writing in common folders, and the software we used had some kind of version control which wasn't really good. But good for collaborative work - allthough slow. 
- Projects with industry. 4-5 from their side and 4-5 from ours

### Poll : Did you create a Github account?
- yes I have an account (add an o) ooooooooooooooooooooo
- yes, I have created one for this course ooooooooo
- not yet o


### Comments

1. I could not follow yesterday, what is the minimum set of commands I could type so that I can follow today?
    ```
    git config --global user.name "Your Name"
    git config --global user.email yourname@example.com
    git config --global core.editor nano
    mkdir recipe
    cd recipe
    git init
    nano instructions.txt # and here add instructions
    nano ingredients.txt # here add recipe
    git add ingredients.txt
    git add instructions.txt
    git commit -m "adding ingredients and instructions"
    ```
    - We have all the commands in the lesson, and also a "recovery" repository that you can start from.
        - Can you share a link for that repository?
        - It is in the materials, no need to prepare early.
        - But it is the note here: https://coderefinery.github.io/git-intro/conflicts/#preparing-a-conflict


2. Q: Have we started yet? I cant hear anything...
    - A: Apparently not yet (08:52:35 CEST)
    - A: Now it has started 08:53
    - We are always a bit late, I think I have it all set up and then realize "oh, I need to do this before we start..."


## Resolving conflicts
https://coderefinery.github.io/git-intro/conflicts/#


3. Q: Can you create a new branch from an older version of your project?  
    - A: Yes.  `git branch NEW_NAME HASH_OF_STARTING_POINT` will start a new branch from that old starting point (which you find from the log)
    - You can also create a new branch based on the old branch (instead of the hash) `git branch NEW_BRANCH_NAME OLD_EXISTING_BRANCH_NAME`
 

4. What does (Head --> Main, origin/main, origin/HEAD) indicate?
    - HEAD is what is currently checked out and where commits get added.
    - So it means "You are currently on the main branch.  If you commit, it will be added to main".  This commit is also `origin/main` and `origin/HEAD` (but if you commit those aren't changed).


5. How does GIT recognize the same 'part of the code'? I think it is not by line number but by context of lines around it, is that so? (Sorry if question is not very well worded)
   - I think it is some combination of offset + replaying all history.  I am not fully sure - but know that these diff and patch algorithms are fancy!  It usually does quite well.
   - Ok thanks!
   - Just to add: it might feel uncomfortable to trust a 'black box' recognizer at first but it does work really well, over the years I have never seen it make a mistake.


6. Why does R's `git graph` not show the names of the other branches? Have they been deleted after merging?
   - I guess so.  We talked about it yesterday and it is usually good practice to delete after you don't need (but nothing wrong with leaving).
   - Deleted with the command `git branch -d [banch names]`.


### Type-along: preparing a conflict
https://coderefinery.github.io/git-intro/conflicts/#preparing-a-conflict


7. Can we get a detailed explanation of this output by git? (after `git diff master dislike-cilantro`). What is `a`? What is `b`? What does it mean that `a` is to the right of `---` and `b` to the right of `+++`? What if `b` deleted lines and `a` had more lines than `b`? Would the minus (`-`) appear regardless?
```git
diff --git a/ingredients.txt b/ingredients.txt
index a83af39..1feeb12 100644
--- a/ingredients.txt
+++ b/ingredients.txt
@@ -1,4 +1,4 @@
-* 1 tbsp cilantro
+* obliterate cilantro
 * 2 avocados
 * 1 lime
 * 1 tsp salt
```
  - "a" and "b" are some sort of references to "previous and other side being compared".  And used below.  This kind of format comes from old diff-format conventions.
      - To be precise: "a" and "b" refer to the arguments in you `git diff` command; e.g. `git diff <item a> <item b>`. In this case "a == master" and "b == dislike-cilantro"
  - `--- a` means "subtractions below are from a", `+++ b` means "additions to b".  `+`` and `- are whatever needed to go from `a` to `b`.
      - subtraction = deleted lines
      - addition = new lines
  - I would not recommend looking at this in detail now, lot of stuff here: https://en.wikipedia.org/wiki/Diff#Unified_format
    - *(OP:thanks!)*


8. What was the alias for `git graph` again?
    - `git config --global alias.graph "log --all --graph --decorate --oneline"`


9. `git add ingredients.txt`
```
$ git commit -m 'decreasing the amount of tbsp cilantro'
On branch like-cilantro
nothing to commit, working tree clean
```
  Don’t know why it didn’t work.
  - It looks like there are no new changes to files (="working tree clean"). Edit `ingredients.txt` (decrease the ammoun of cilantro), stage with `git add ingred*`, and commit.


10. How can I search in nano editor?
    - CTRL-w
    - it should be visible in the menubar below (`^W Where is`)


11. Please try to slow down in type-alongs a bit.(+2)
    - Thank you for the feedback.


12. When merging, should I note that this was a merge in the commit message?
    - Git usually suggests an automatic commit message for merges. It says at least that this is a merge commit and gives the two commits being merged.
    - 9:33 In general yes, simply to recall what you did way back then when you return to the history after a while.


13. Why wasn't there a conflict with the first merge of `like-cilantro` and there was only with the `dislike-cilantro`?
    - The first merge was like-cilantro→master.  There wasn't the same change in `master` yet, so nothing to conflict (yet).
    - Git is good at figuring out things on its own (which part of the code is newer, how to intergrate two different changes). conflicts occure, when Git can not figureout, on it's own what to keep and what to discard without loosing anyof the contributions.
    - Conflict is when two commits want to do two different things in the same place; if this does not happen there is no conflict. That means that the changes are in different parts or in a new part of the document. So be aware to check with `git diff` before you make a `git merge`, before it goes too fast.


14. It was really difficult to type along, listen, and comprehend the complex material.
    I think it would have been better if we were not instructed to type along but focus on listening to the explanation. But we can also watch the video. 
    - Would it be better if the "type along"s would be "watch first and then type (with a small pause in the instruction stream)"? Or worth a try. -- YES
    - Or give option "either type-along if you are comfortable, but if it goes too fast you can watch."
    - I can manage type along with Github, it seems. It is not that complicated


15. Google drive conflicts: once I tested, and if you try to do two things at once (like in Google Sheets), one side just gets lost!
    - That's annoying.


16. I don’t see anything after typing recipe `git diff master dislike-cilantro`.
    - Is it already merged?  If so, there will be no differences, and you would get nothing out.
        - In the instruction, merging comes later.
            - When you don't know what happened, it's a good idea to use `git graph`, `git status`, and/or `git diff` and try to clarify the changes in different commits. +1


17. Can you zoom In??
    - Is it good now?
        - Yes, thanks :smile:


18. If I type `git commit` without any message I get indeed this file with a standard commit message, but I cannot make changes to this screen or exit this? How to do this? I use nano for my normal use, but the git commit does not seem to be in nano. Edit: I cannot directly check as I already merged them, but I think it will work; nano was not the default editor. Thanks!
    - If you can not write, it has probably opened vim :) Try this command: git config --global core.editor "nano" and then git commit, any difference? edit: OK! Edit again if the problems linger.


### Sharing repository online
https://coderefinery.github.io/git-intro/remotes/


19. Is this type along or do we just watch now?
    - Type-along
        - lesson: https://coderefinery.github.io/git-intro/remotes/#type-along-create-a-new-repository-on-github
        - go to your GitHub account, click "new" repository (green box), and continue with the steps in the link above. 


20. Can we change these GitHub settings later?
    - All the settings can be configured later. (excluding git history) 
 

21. What does `push` mean?
    - "Commits on my side, they get sent somewhere else.  Some branch somewhere else updated with these commits."
    - Simply put "push ~= publish my local changes"
    - (The opposite is "pull", getting changes from remote repo to your local one)


22. So is the agent pulling and pushing stuff always the local repository?
    - Pulling from remote to local repository, pushing from local repository to remote one.


23. Are you teaching how to clean up/delete existing repositories in our GitHub accounts later?
    - yes we will show that (settings, scroll all the way down where you can remove repo)


24. So far we are working on one directory that only contains files, what happens when working with a directory that has files and several sub-directories? Which is the 'main' branch? 
    - The directory that was initiallized with `git init` and all its subfolders are part of the repository.


25. On Mac it seems the dialog is quite different. Don't get to choose private or public for instance
    - This is the web interface?


26. Should I type "master" instead of "main"?
    - If the branch is called "master", you should type "master" instead of "main"
        - git has officially changed the naming convention of the primary branch from "master" to "main". `master` is the legacy name for the primary branch.
            More recent git versions default to `main` -branch name convention (src: [Github Blog Post](https://github.blog/changelog/2020-10-01-the-default-branch-for-newly-created-repositories-is-now-main/) )


27. Too fast. What did she do after entering the commands?
    - refresh/reload the github page after typing the commands


28. I get error: fatal: unable to access 'https://github.com/coderefinery/recipe-after-merge.git/': The requested URL returned error: 403. when trying to push
    - You cannot `git push` to the main branch of the `recipe-after-merge` remote on `coderefinery`. You should `git push` your changes to one of your own remote repositories.


29. I am on Gitlab instead of Github, and these are my commands to push an existing folder:
    ```
    cd existing_folder
    git init --initial-branch=main
    git remote add origin git@git.app.uib.no:MyName/recipe.git
    git add .
    git commit -m "Initial commit"
    git push -u origin main
    ```
    Is that just several ways of doing this?
       - These are pretty similar, above it also shows how to make the whole repository if it didn't exist (init, add, commit)
       - A shother way is to clone the repository with `git clone`

30. I get the following error: 
    > fatal:git@github.com: Permission denied (publickey). Could not read from remote repository.
    - SSH keys are not set up: **https://coderefinery.github.io/installation/ssh/**
    - There is probably not enough time to debug now, you can watch this and the next section won't need it, and then you can check later today.


31. Follow up question: How can I check that the key is there? Or which one? I'm pretty sure I have a key installed/set up.
    - https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys


32. Im getting 
    > error: remote origin already exists.
    - Did you do the recovery step (cloning the existing repo)? `git clone` will define the origin by default, so you need to redefine it if you want to save your repository to a different remote one (see below).
    - Easy solution: delete the existing remote: `git remote remove origin`.  


33. So if my local branch is called master do I still go 
    ```
    git branch -M main?
    ```
    - No, replace "main" with "master". 
    - This is a requirement of GitHub that does not find the 'master' attribute politically correct


34. Could we make a break soon so that people could resolve some issues in groups?
    - Probably coming soon


35. How to push with all branches?
    - There is an `--all` option, and some configuration options.


36. Where do you find the remote command?
    - What do you mean?
        - The `git remote add` command I mean with the correct address.
            - `git remote add origin git@github.com:username/recipe.git`, where username should be replaced by your GitHub username. Also, you need to have created the `recipe` repository on GitHub before this. You may replace `recipe` with a repository name of your choice.   


37. I get an error saying: 
     ```
     The authenticity of host 'github.com (...)' can't be established.
    ... key fingerprint is SHA256:....
    This key is not known by any other names
    Are you sure you want to continue connecting (yes/no/[fingerprint])?
    ```
    - "Yes" the first timee, then it will remember.
    - A more security oriented way would be to check that the finger print listed here matches the fingerprints of the `github.com` official listed fingerprints (found [here](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints))


38. I have fatal error message saying: 
    > git@github.com: Permission denied (publickey).fatal: Could not read from remote repository.Please make sure you have the correct access rights
    and the repository exists.
    
    - Check #30 above - ssh key setup


39. I get this message for  `git push -u origin main`: (+1)
    ```
    The authenticity of host 'github.com (...)' can't be established.
    XXXXXXX key fingerprint is XXXXX:
    XXXXXX.
    This key is not known by any other names
    Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
    Warning: Permanently added 'github.com' (XXXXXXX) to the list of known hosts.
    git@github.com: Permission denied (publickey).
    fatal: Could not read from remote repository.

    Please make sure you have the correct access rights
    and the repository exists.
    ```
    What should I do?

    - See #30 above - ssh keys need to be set up, probably not time now.  Watch, the next section won't need, and you can set up later today.


40. I am using triton and getting this: 
    > Permission denied (publickey).
    fatal: Could not read from remote repository.
    - See #30 above.

41. 
    > git@github.com: Permission denied (publickey).
    fatal: Could not read from remote repository.

    Please make sure you have the correct access rights
    and the repository exists.

    how can I do so?
   
    - See #30 above.
 
 
42. I get asked for pass phrase with each push with SSH key. Can this be turned off? It's not there when using https.
    - Yes. It is normal. SSH passphrases protect your private key from being used by someone who doesn't know the passphrase. Without a passphrase, anyone who gains access to your computer has the potential to copy your private key. I would not recommend to use SSH keys without a pass phrase. But is is possible not to use one, more info here: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/working-with-ssh-key-passphrases.

43. If I already typed `git branch -M main`, can I change it back to master?
    - master may still exist.  `git checkout master` will go back to master, maybe `git merge main` will sync it with master.  But I might recommend going through this wth someone
    - master does not exist, but I am fine working with main
        - Type `git branch -M master` to rename back your branch if you wish.


44. Can you explain these commands again?
    ```git
    git branch -M main
    git push -u origin main
    ```
    - First command renames the current branch to `main`
    - Second command pushes `main` to the remote (other repository) set up as `origin`.


45. I get this error:
```
fatal: not a git repository (or any of the parent directories): .git
```

when I want to run

```git
git remote add origin git@github.com:user/recipe.git
git branch -M main
git push -u origin main
```
- It seems you are not in a git repository currently.


46. error: remote origin already exists.  

    - See #32 above, you need to redefine your remote `origin`.
    - `git remote remove origin`


47. I get an authentication error while I'm entering my username and password correct. I've tried multiple times.
    - Github doesnt' work with password from the command line.  See #30 above.  I recommend watching for now and setting up later today.
    - You can find how to test your GitHub + ssh in the workshop preparation page: https://coderefinery.github.io/installation/ssh/


48. Isn't it recommended to leave the merged branches in the graph so that you can track when a potential mistake was made and to be able to return to a previous version? Don't you lose this possibility when you delete them?
    - Up to you.  I usually remove, if I look for the merge commit it will say what branch was merged, so can recover that point later on.


49. If you do this task next time, please make people check if their SSH is working. This is a bit frustrating. Because I am sure that I set it up like the manual before, but it is still not working and following without clicking along is a bit... sad. 
    - For anyone wondering how to test GitHub and SSH, see pre-workshop instructions https://coderefinery.github.io/installation/ssh/
    - If you can figure out why the instructions don't work, please let us know!  We should fix them.


50. The color coding (for indentation) in this HackMD seems to be broken - is it possible to get it working? I accidentally answered questions cause I didn't notice they already had answers in grey/blue (not red).
    - Thanks for letting us know.  It's not perfect, we don't have time to fix it live - but will try more.
        - Understandable :)


51. So now only the main was pushed to the server, how do I add my banches also?+1
    - `git push --all origin` This will push all branches to origin. Defined tags too.
    - You can also push a particular branch: `git push origin <branch-name>`


### Break until xx:15
Then we will look at history inspection


52. should we go back to master? because we switched to main when we were pushing
    - If you originally had a branch called "master", I would recommend switching back to it. Not sure that using "main" will no cause a problem. 
    - To do this, run `git checkout master` and then `git merge main`
    - Thanks
    - But master was renamed main, so `git checkout master` does not work anymore because the master is now main
    - In the end, this doesn't matter for the rest of today.  In the long term, either works.


53. When I try to push the recipe folter to github, I get a authentication popup where i try to authenticate, but then the following happens, what would be the fix for this? SSH seems to be set up correctly
    ```
    remote: Permission to coderefinery/recipe-after-merge.git denied to user
    fatal: unable to access 'https://github.com/coderefinery/recipe-after-merge.git/': The requested URL returned error: 403
    ```
    - It looks like you're trying to push to the repository on the coderefinery organisation. Probably you do not have permission to do that ( you need to be added as a collaborator to be able to push, also in a public repository)


54. If other ssh exist but still do not manage to push. Should I try creating a new one? (following this: https://www.youtube.com/watch?v=XCDg1mtaA5I&list=PLpLblYHCzJACyKCfHnPwRruOxllNoHsEg&index=3&ab_channel=CodeRefinery)


55. 'Enter passphrase for key' means github password?
    - It is different. It is something you chose when you set up the ssh keys.


56. When I test ssh connection with 'ssh -T git@github.com' it gives the correct connection message, but when I try to push the repository then it asks me for my github username and password, and then it says that support for password authentification 
    - What does `git remote -v` say (please remove your username from the paste) 
    - origin  https://github.com/user/recipe.git (fetch)
        origin  https://github.com/user/recipe.git (push)
 
 
57. When I type the command, it shows 'error: remote origin already exists.'
    - You already have a remote address with the name "origin". If it is the correct one, you don't need to do anything. Check with `git remote -v`
    - If the remote you have is not the correct one, run `git remote remove origin` and try adding it again. (You can do this in any case if you want to try it.)


58. Solved a problem (even with ssh key was asking for a password) for me https://mkyong.com/git/github-keep-asking-for-username-password-when-git-push/
    - Great that you found a solution! In practice this is the same as our preparation materials, i.e. make sure that we use "ssh" for the remote of the repository (not https) and working ssh-keys. You will still have to type the ssh passfrase, we have a nice video on how to setup a ssh agent to avoid typing the passfrase too often https://www.youtube.com/watch?v=-TXld8Nx76Y
    - To debug ssh keys issues you can run `ssh -Tv git@github.com` which will show for example if a key is not found.


## Inspecting history
https://coderefinery.github.io/git-intro/archaeology/#


59. Why in this part we git clone with https? Just curious.
    - We don't need to push later, and https has less risk of problems (see questions above).
    - (if I cloned with https and needed to push later, I would change the remote to ssh)
    - because this works also without setting ssh keys and we don't need to contribute anything back. so it's
      safer but also possibly more confusing since we said earlier that we shouldn't use https to push
    - so in other words, if I am sure I only want to clone but never push back, I usually use https


60. What does the `-i` do to the grep command? And does it work as well with the "normal" grep?
    - "case insensitive" - `A` is the same as `a`.  Yes, it works for normal grep.


61. Where do `grep` look for the text? In the commit messages or in GitHub in-line comments? or both?
    - Current versions of all files.  Different options search within commit messages or historical versions of files.


62. What is the difference between simple `grep -R` and `git grep` ? 
    - `git grep` searches only files tracked by git.  `grep -R` would search all files in the current directory (including the `.git` directory, which has a bunch of stuff in it).


63. how do I exit from git show after"END"?
    - does `q` work? --> YES, thanks! 


64. Can you show again how to use annotate in the browser
    - Go to a reposity, then a file in that repo, and click on "blame". `Blame` provides the same output as `annotate`. Found it? - Yes thanks.


### Exercise: archaelogy until xx:05
https://coderefinery.github.io/git-intro/archaeology/#exercise-basic-archaeology-commands

Goal: History-1
Optional: History-2

Then we will do a break.

I am (choose all that apply):
- done: ooooooo
- not trying: 
- day is too slow: 
- day is too fast: 


65. Does `grep -i` works only on HEAD? or on other branches/commits too?
    - Default is HEAD. But you can also search through all past commits with `git log -S` (it's mentioned under git grep but I jumped over it to not throw too many things at learners)
    - `git grep PATTERN HASH` will search PATTERN in some old commit HASH.


66. Can you provide an useful/interesting example to use with `git log -S sometext`? I went through the documentation and it is not so intuitive to understand how it can be useful.
    - If you use some keywords like "fixes bug #2", "breaking change" and so on, you can search for those.
        - Sorry, I mistook it for the one that searches commit messages :thumbs_up:
    - but `git log -S` searches through tracked files, not commit messages. It's a useful command to search for commits where particular code (e.g. functions that you know the name of) got introduced or removed
    - If you notice that a functions does not exists, but should, you can check when it was removed and get the text of the function from the past commit.


67. After running git grep the terminal freezes, and I cannot exit by using q or control z/ d/ c, it does however provide an output. Anybody else has this problem?
    - One common issue is pressing ctrl+s by mistake, which freezes the terminal. Try ctrl+q when the terminal freezed and your not sure why. (s stands for stop and q stands for quit)


68. After running git annotate, I am note able to search the file using "/Logic error". Only thing that works is exiting using "q", but then I am not able to search the file anymore.
    - what happens when you hit "/" --> That worked, thanks!


69. I am trying to set up SSH connection. I am watching the video linked. But it looks like I already have it set up. 
```
 ls ~/.ssh
id_rsa		id_rsa.pub	known_hosts	known_hosts.old

But I did get this error message when we were working with Github this morning
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```
  - Hm, so `git` is finding some other version of ssh.  Do you anyone local you can look at it with?
  - and the public key is uploaded to github?
  - `ssh git@github.com` shows your username - I guess so, you said it the verification worked.

  - I am working home alone. I have had an (inactive) Github account. I don't remember if I have uploaded my SSH key before or not. How can I check it?
ssh -T git@github.com
git@github.com: Permission denied (publickey).

  - Can I get help with SSH?
      - what university are you at?
  - https://coderefinery.github.io/installation/ssh/
  - I watched the video but did not help though. I was at JYU until recently. 


70. In the last part of returning to the previous commit, the -1 after the hash failed:
    ```bash
    fatal: ‘90544b4fa-1’ is not a commit and a branch ‘just-before’ cannot be created from it
    ``` 
    - it should be "tilde" 1, `~1`
        - Thanks


### Break until xx:16


71. Does ```git log -S "Logic error"``` show the last commit where the file containing "Logic error" was changed?
    - it should show all commits where "Logic error" was added or removed
    - so if it shows only one commit, that's where it was added. If it shows two it'll be the commits where it was created and then removed


72. I found the string `Logic error in degree_correlation` in the file `networkx/algorithm/threshold.py`, current line 543 for the networkx-2.6.3 version. The command `git annotate` `networkx/algorithm/threshold.py` tells me that that line was modified in the commit `90544b4fa` on the 2017-08-17. But if I run `git log -S "Logic error in degree_correlation"`, it gives back the commit `4dff462e5` on the 2005-08-03, which is also the last commit that modified line 544 of the same file. Nevertheless if I look for `git log -S "print(\"Logic error in degree_correlation\", i, rdi)"` it gives me back the fist commit (`90544b4fa`). Why is it like this? It seems that this line was originally added on 2005 (I checked it) but the last modification happened in 2017 and depending on the string I provide, `git log -S` answers with different things. I recommend to try these commands before answering.
    - OP: **I found out the issue** The `print("Logic error in degree_correlation", i, rdi)` existed from 2005, but in 2017 spaces were added after the commas. So depending on if you introduce the spaces after the commas of the `print` command, the results would be different.
    - Explainer: `git grep -n "Logic error in degree_correlation"` returns the expected result. You gave a wider search pattern, so you also picked up the line where the line was created (4dff462e5). `git show` shows that commit 90544b4fa specifically introduces good typesetting practices for Python (PEP 8, if you are curious of what they are: https://pep8.org/), that's why spaces matter.
    -  +1, I had just noticed that but the commit hashes were somehow different so I wasn't sure.
    - +1


73. The task was a bit confusingly worded, "how could you bring the code to the commit..." --> it made me at least think I was supposed to do some sort of merging :D
    - Thanks!  I just submitted a pull request (we'll learn them tomorrow) to improve the wording.
       - thank you!!!


74. I have a problem with `git annotate <file name>` where everything is immediately printed out and return to command line.
    - So there is no pager that lets you scroll around, right?
    - Yes!
    - Did you do these steps?: https://coderefinery.github.io/installation/shell-and-git/#on-windows-git-log-git-diff-git-branch-or-other-git-commands-show-no-output-at-all
    - I did
    - Try `git --paginate annotate FILENAME` and see - this tells it to use the pager.  Though if the pager didn't work before, it probably still won't work now.
    - I just tried. It did not work. I will look more closely into the guide and see if I skipped a step.
    - OK, I'd recommend finding someone local to help take a look and see what is wrong/a better solution and we can add to our instructions.
    - Thank you.

75. Maybe useful to add info how to go out from git bisect mode in the optional exercise:  `git bisect reset`
    - thanks. yes.
    - I made an issue about this, thanks.


76. Not a question but another way of checking the last commit for a specific line is is by using git blame in command line: `git annotate -L <line_range_start>,<line_range_end> filename`, so in this case, `git annotate -L 543,543 networkx/algorithms/threshold.py`.
    - thank you, nice to know


77. If you use git graph now, it shows all commits (up until the current commit in 2022), while git status only shows previous commits before 90544b4f. Is that expected?
    - Yes.  The `git graph` alias includes `--all` that means "all history".


78. How do I get `git bisect run` to execute a Python script? Wrap it in a bash script?
    - I think it can do anything that can run from the command line - no extra wrapping needed.
    - it needs to return zero or non-zero but can be python
    - `git bisect run python my_script.py` for example. The command after `run` can be basically any command line (note: you need to first start the bisect and mark good/bad commits)


79. #69 wishes to have a bit more solutions to the problem....
    - we can also try to zoom-call after the lesson and debug on screenshare? 
    - Sounds good. Thanks. I left the lecture because I could not follow anymore, but wants to have SSH set up for tomorrow (I will catch up on the material from today later today)
      - it's pity since we did not need ssh for most of the rest (and we should have communicated that clearer) 
    - what university are you at?
    - How can we do zoom-call after the lesson? 
      - RB: my afternoon schedule is unfortunately full but perhaps send an email to support@coderefinery.org and we see what we can do? in that email please describe what you have tried and what the error was. but I will also read up here and on question 69 


### Undoing and recovering
https://coderefinery.github.io/git-intro/recovering/


80. Instead of `restore` I could also just `checkout` the file again?
    - yes, `git checkout somefile` has the same effect


81. For me `git restore` does not work:
    > git restore  
    > git: 'restore' is not a git command. See 'git --help'.
    > 
    > The most similar command is
	> remote
    - Too old git version.  There is a reason we don't expect git restore
    - Follow up: is there than another command? `git checkout`
    - It is still there for me if I try to do that with `git checkout`.. So I needed to change it manually.
    - We are soryr for the trouble, I didn't know that it had `git restore` ~~by default~~ as the default option in the lesson materials.  We tried to keep it compatible with old versions to avoid confusion.
    - What do you mean by default? Does it mean if I check out of the branch into another one it "resets" automatically? So if I want to do it, I just need to change branches instead of using `git restore`
    - I am a bit lost here.  Maybe resume after the workshop?  what university are you at?
    - does the `git restore --staged .` followed by `git restore .` help anything? (this would be the command if a file was `git add`ed)
    - Was not staged, these comments do not work as well. But I will try to solve it later with people here. 
    - Solution: there was a communication "problem": use `git checkout file` not for the branch!


82. Could you please show one more time how we can compare two commit on the github?
    - was it the "git show" on github? if yes, then compare "git show 90544b4" with https://github.com/networkx/networkx/commit/90544b4
    - also try that on a different repository (and different commit)


### Exercises: undoing and recovering, until xx:00
https://coderefinery.github.io/git-intro/recovering/
Goal: at least try out Undoing-1 and Undoing-2.  But if you can't, it's OK.  Work on whichever ones seem most interesting

83. Will you repeat which exercise are going to be done in breakout rooms? I am confused.
    - we will above
    - thank you!


84. How can I go 2 or more steps back?
    - this modifies history:
      - i would first "back up" the commit by creating a branch to it
      - then: `git reset --hard` back to the commit where you want to "rewind" your branch to
    - Do you want to rewind the branch (lose history), or add new history that undoes the previous? 
      - I was in the master/main branch, thus I don't want to remove it but I was wondering what if I make two mistakes in the row without realizing, if I recover once I will go only one step back, so how I reverse the second one as well? 
         - safe way: first revert the older mistake, then revert the newer mistake. this creates two new commits
      - `git reset --hard HASH_TWO_COMMITS_BACK` will wipe out those two commits (modifies history, warning).  The previous point is the way if you dont' want to modify history.
        - the previous point is the same though git reset --hard. So how do I not modify history?
        - `git revert OLDEST_COMMIT`, then `git revert SECOND_OLDEST_COMMIT`, and so on.  History preserved, only new commits added.


85. How do I fix this?
$ git revert ae36511
error: commit ae36511952ce004f98b4b49bef70c96e409a00a5 is a merge but no -m option was given.
fatal: revert failed
- Try to revert the commit that was merged, not the merge commit itself.  (this is the simple option)
   - it is possible to also revert merges with `-m` but I recommend to practice on "simple" commits, not merge commits for the moment +1


86. What was the difference between those short (7 character) hashes, and the the long ones?
    - It was just me being lazy. They have same effect. You can refer to their beginning if the beginning is unique and with 7 characters it often is.
    - You can use any number of characters that uniquely identifies the hash in your repo.
    - Because the hashes are essentially random, the chance of two hashes in the same repo starting with the same 7 characters is very very small. If you have only a few commits, even 2-3 characters can be enough.
    - And I think it also starts showing more characters by default as the repo gets bigger.


87. In the paragraph "recovering from committing to the wrong branch", I understood that you use cherry-picking if you want to select a few commits of the "wrong branch" to move to the "good branch", and thus keep some commits on the "wrong branch" that actually belong to the "wrong branch". But why do we then use git reset --hard in step 4?
    - The commits were "copied", not "moved", so they stay in the branch where from they were copied. You need to switch to that branch and remove the commits from there if you don't want to keep them.
        - Follow-up question: But then all other commits are also removed, the ones that you wanted to keep on the "wrong branch".
            - Yeah, so then you need to be more fancy than `git reset --hard`.  I would use `git rebase --interactive` and you can do a lot with it - search the web for "git rebase interactive drop some commits" and you can probably find explanations of how to use it.
                - with git, you can do anything... but you may need to study some for it.



88. After typing 
```git
    git reset --hard dd4472c
```

I see this when using git graph: 
```
    *   0380472 (origin/main) Merge branch 'dislike-cilantro'
    |\
    | * 2bc5166 (dislike-cilantro) reduce cilantro
    * | c0b5f6e (like-cilantro) increase amount of cilantro
    |/
    *   23c0351 Merge branch 'less-salt'
    |\
    | * bf59be6 reduce amount of salt
    * |   e02685c Merge branch 'experiment'
    |\ \
    | * | 6feb49d maybe little bit less cilantro
    | * | 7cf6d8c let us try with some cilantro
    | |/
    * / 40fbb90 draft a readme
    |/
    * dd4472c (HEAD -> main) we should not forget to enjoy
    * 2bb9bb4 add half an onion
    * 2d79e7e adding ingredients and instructions
```
I expected that everything above `HEAD` would disappear. 
Did I do something wrong?
   - It worked.  `main` got reset back to that commit, but the other branches still exist (origin/main, like-cilantro).  Since `graph` uses `--all` in the alias, it still shows all of these other (still existing) commits.
     - `git reset` modifies current branch but does not modify other branches
  - Commits will "disappear" only after no labels (like a branch or tag) points to them, or any of their successors.


89. Is there a way to modify a commit that is not the last one? like three commits ago (with `git commit --amend` or other command)
    - Advanced: `git rebase --interactive` can do this.  I recommend you search the web for `git rebase interactive squash`
       - with that you can delete, reorder, squash, split, ... everything
        - `git rebase --interactive` allowed me only for changes that I made today in the file, can I make changes to even older commits? 
            - It can go as far back in history as you want.  But if you change some old history, and someone else has that history, you now have divergent history and that is *bad* - you will need to work that out.  In practice, it's not possible in big enough projects.
                - so in that case should I make a new branch and merge it with the old one?
                    - Hm.  If you then merge, it will keep the stuff you just removed.  I would say, if you are rewriting history from that long ago, use "revert" (preserves history) unless there is confidential data in there.  Try very hard to avoid that!


90. I tried saving the hash before and after using `git commit --amend`. Both can still be used with `git show <hash>` afterwards, but only the changed is present in graph.
    - Good point!  So, the way git works, hashes are unique and the old hash/data still exists (until it gets automatically cleaned up later).  You can `show` the commits that aren't accessible from any branch to see/recover old stuff.
        - Nice! When will it automatically be removed? Upon console closure?
            - Running `git gc` will manually "garbage collect" old stuff, and the official doccumentation says: "When common porcelain operations that create objects are run, they will check whether the repository has grown substantially since the last maintenance, and if so run git gc automatically."
            - Default seems two weeks ago (from manual page)


91. How do you update the Gitub code for recipe if you have changed it locally?
    - 1. Define a remote, if not done already: `git remote add origin https://github.com/user/recipe.git`
    - 2. `git push` with the right options.
    - If you have changed history, you need to `git push -f` to force-push it (otherwise the push will be rejected).  This will change the public history - if anyone else works on tihs project, there is a big danger of confusion.  Make sure you know what you are doing.


### Break until xx:10


92. I get a strange error: Found a swap file by the name "~/recipe-after-merge/.git/.COMMIT_EDITMSG.swp". Not sure what this means but it does not let me amend and throws this error every time...
    - I would try deleting this.  This is an editor backup file.  You could also check if you have any other commits in progress and make sure those are closes.


93. Why would the revert fail? Even if its the last one.
    - If you revert the previous commit, it should always succeed.  But if you revert something from further back, and other commits have changed the lines... then you will get a conflict to resolve.


### How much Git is necessary?
https://coderefinery.github.io/git-intro/level/


94. To be honest, I am quite often using only main in my personal projects. +2
    - I sometimes use git only to track my workflow and do back-ups (for example on LATEX documents)
    - +1 this is perfect!


95. I suppose it's possible to have a private repository which you can share only to the people you trust - like in a case where I have business secrets?
    - Correct, this is a common use case.


96. If I understood correctly, I can use Visual Studio to do all of this if I want...but for the sake of this course's clarity (I'm a noob) it's better that I used this shell and nano. So my question is that if I configure Git Bash to use Visual Studio, can I use all of these commands inside Visual Studio? (Or do I have to do the git stuff through the command console)
    - vscode probably has git built in, but yeah, the commands and repository should be usable in both vscode and from the command line - same repository (afaik: you need to install the extension and then you can use it, it has also visulazation for graphs in some extensions)


97. What about licencing before making it public? Is it safe? very briefly, how  does that work?
    - Very important question, we have a session on next week.  It depends a lot on where you work.  And who all contributed.


98. Should I commit secrets?
    - If you do, that repository is secret forever (since it is in the history).  It is not recommended unless you want that.
    - But tracking secrets is often good!  So consider one public repository, and one dedicated secrets repository with only the secrets, that is kept secure.


## Feedback day 2

Today was:
- too fast: ooooooooo
- too slow: oooo
- just right: oooooooooooooooooooooooooooo
- useful for my work: oooooooooooooooooooooooooooooooooo
- boring: 
- recommendable to others: ooooooooooooooooooooooooooooo
- I should have done this years ago: ooooooooooooooooooo
- I knew some of this, but it was nice to see what I missed before: oo


One good thing about today:
- I used git, but it was very useful to learn how to revert to earlier commits +1
- Recovering from committing to the wrong branch is very interesting. Good to have it written down. Would be nice to see it in more detail though. +1
- Having time to test the tasks and run into small problems and fix them or learn how to use comments. 
- very useful material! I will keep on going back to this! (+3)
- I'm happy that I decided to participate, I didn't know where I'd exactly need this stuff but now I know.
- getting some tips on how to actual use git (especially the last few minutes "how much git")
- You're doing great guys!! Thanks for all the clear info
- Really good to get a proper overview of how Git works, previously I've googled single commands but never really understood the context
- Git bisect automation with a script was new and useful to me.
- `git log -S` that a killer feature

One thing to be improved for next time:
- I missed a memo to have SSH keys sorted and Github account created, making it more clear would be useful
    - I think just having one minute for everyone before a break to check if their SSH works and then post the link for people to figure it out. 
- I think SSH keys are common issue ( some people have them but still doesn't work) - maybe a good idea for the future is to compile a list of potential issues and solutions (+1)
  - We have really tried to make this clear in the install instructions, but ....
  - Could have per-day links to ¨remember this bit of the install instruction for this day¨? in the schedule or beginning of HackMD
  - Also I mean troubleshooting instructions - it's only anecdotal, but it's the 2nd time I join the CR and the second time I have people in my group that already have SSH configured and `ssh -T git@github.com`  works fine, but there's something wrong with the configuration. but maybe I was unlucky and it's not a common problem.
- some more just demonstration (explitly not type along) for real world applications would be cool
    - (I am staff) +1

Thoughts on online format:
- I think sometimes for the type alongs it would be nice to have quick check-ins for the people who are together some where to check if they work out, because if someone got stuck somewhere it is a bit hard to continue following (+2)
- Doing the exercises by ourselves/on teams and then going through them again all together seems a bit redundant, especially if the solution is already on the website.
- Shorter theoretical time and more hands-on would be beneficial. Some links to how to use the command promt and nano might we welcome for some people attending, which slows down the hands-on sessions.
- Great to have helpers/ exercise leaders on Zoom Breakout Rooms 

Other feedback:
- I really like that there are so many exercises to try out commands. On my work projects, I am often worried I'll break something and steer away from git commands I am not 100% certain about.
    - As long as you `git add` (and preferable `commit`) at least once, you can usually recover - but you might need to ask for help!
- It was difficult to follow because I was unable to attend yesterday. Fortunately the study material is available for me to practice later. Also, I'm happy that I sort of got the hang of what's happening and succeeded in the exercises in the end.
    - Great!  Yeah, it's sort of "choose your own path" and it's completely OK to watch and follow up later.
- There are some gramatical errors and sections in the material and exercises that are difficult to interpret. 
  - Please let us know!  Easist way is to make an issue on Github (top has an edit button, then you can go to Issues and make it).  Tomorrow, we will learn how to open a pull request, which can also be done through the web interface.
  - and I'm opening issues for issues that I see in the notes above.

