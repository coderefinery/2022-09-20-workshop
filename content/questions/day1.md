+++
template = "page-with-toc.html"
title = "Questions and notes from workshop day 1"
+++

## Icebreaker question

:::info
Add `o` after the option that describes your situation
:::

1. What is the operating system on the computer that you will use during the course?
	- Linux: oooooooooooooooooooooooooo
	- macOS: oooooooooooooooooooo
	- Windows: ooooooooooooooooooooooooooooo
	- Other:
		- (name here)

2. How did you learn to program?
	- At my university Fortran introductory course in theory. In reality self taught to finish all the assignments.
	- I'm self-educated.
	- I took some coding courses during my bachelor and master.
	- I followed some courses in modelling and simulation during my master.
	- During my bachelor of psychobiology and now learning a lot during my Ph in computational neuroscience, but I feel like some of basic knowledge is still lackingD.
	- I am creating a small inversion script for my PhD in Geophysics.
	- I am a master student and I need to review my `git` knowledge.
	- It looked cool and started writing scripts on Windows 95 and MSDOS when I was like 10. Eventually I learned to use a compiler and started to program in C from a book from Deitel & Deitel.
	- Started learning at school back in the early 2010s. Really started to get a hang of it as a research assistant.
	- I was doing my bachelor and I had to submit 700 molecular calculations to a supercomputer and I did not want to write the input files by hand.
	- Undergrad course in C.
	- For my PhD position I needed to learn R.
	- 10 PRINT "HELLO, WORLD"; 20 GOTO 10 on a C64 a long time ago.
	- During last year of high school I learned VisualBasic for Excel.
	- At school (mainly html back then), during an extracuricular activity and during classes (with delphi...).
	- My PhD project is about high performance computing. Starting from Matlab, then Fortran, now trying Julia. Every time I look back, I find my code sucks!
	- I started coding in the final year project in my bacholer degree. My coding is very basic...
	- BSc from Aalto university (Scala)
	- In my Physics Diploma in C and then Matlab. Now I am using Python.
	- Matlab during Bachelor, C++ during side-job.
	- I learnt to program during my high school years starting with C.
	- During my engineering program in university where we mainly used Matlab but also a bit of Python.
	- Started in school, then just continued for fun and later as part of my university studies and research.
	- With my first bachaler course, C++.
	- I learned Python during my bachelors, the basics needed for engineering. I incresed my skill since then slightly.
	- During my bachelors, while everyone was learning MATLAB. I just thought that I want to do Python and did all the exercises on my own ; later we also learned Fortran during the bachelors and used it for climate modelling; added C basic during my doctoral studies.
	- I started during my time at highschool with Pascal in an informatics course, and later added Fortran and Matlab at university. Even later, I went into graphic programming with LabVIEW..
	- BASIC in the 80s: I used it to draw  the silhouette of a Ferrari F40, I think
	- While I was doing my physics degree.
	- Matlab at the university, Fortran for my MSc, and then Python for pre-and post-processing of results in my job as an engineer.
	- I started learning Matlab during an university course in numerical techniques.
	- Via a programming course at university.
	- I started programming in my bridging programme where I made human muscle models in Matlab, then I learned a bit of Python and javascript as well.
	- Logo in primary school.
	- During my master (TCCM) we learned Fortran and then I moved to Python for my PhD.
	- When I started my Bachelor degree at Aalto.
	- Self study.
	- During my masters, I started with Fortran 77. Then, during my postdoc at Aalto, I have been learning/using Python.
	- As a compulsory part of computer science and signal processing studies.
	- Pascal at high school, then Python and Matlab during undergrad studies and later for PhD and postdoctoral research.
	- Compulsory Python course during Bachelor program.
	- R for my dissertation in neuroscience, basics in Matlab.
	- I don't really know how to program but I'm trying. - Started as self study for fun.
	- Python course.
	- During university courses (Java and Fortran) and self study (Python).
	- I started with programming at University, mainly with MATLAB. Now I need more advanced programming skills.
	- I developed an interest in coding through the mandatory programming courses in my bachelor's, chose to minor in it, and now I've moved on to studying machine learning in my master's.
	- During my undergraduate study and started from C++ programming, but later mostly used Matlab.
	- Undergraduate course of C++.
	- Started with old school QBasic as a kid, then started again much later.
	- Self taught.
	- In university studying fluid dynamics and population dynamics learned Matlab. Later at work Python and some Fortran.
	- Online Java course at university.
	- During master course in Matlab.


## Icebreakbreaker and intro

- ## We will use this for collaborative notes and questions.
1. Q: How can I ask questions?
	A: *To write on this document, click on the :pencil:
	(Edit) icon on the top bar and write at the bottom, above
	the ending line. If you experience lags, switch back to
	"view mode" (eye :eye: icon)*
	A: Write your question under here (number questions)

2. Why do we use miniconda, while pip provides all the software required for this workshop?
	- To create an isolated programming environment for a specific project
	- because pip might at some point not be enough.
	- pip also requires a little bit more familiarity with python environment than anaconda and for many learners this is really the first contact with python/terminal/dependencies
	- pip itself is also not contained, i.e. you can't have two distinct environments for different projects with pip and you'll need some environment system
	- pip is a victim of python 2/3 split, perhaps

3. Do I need to join in a Zoom?
	- You may if you got the Zoom link. It is helpful to do the exercises in a team, but it's not a must.
	- Also totally ok to try the exercises on your own. weation via stream for everybody. let's see how this will go. so no problem.

4. I signed up late so I didn’t get a zoom link, is it possible to get one now?
	- We do not have enough helpers for everybody. So for late registrations please follow Twitch only and do the exercises on your own. But please ask questions in HackMD whenever you need help.
	- see also 3. it's not a problem and you will get most of the workshop even without zoom exercise room.


## git-intro
https://coderefinery.github.io/git-intro/


5. Which software is being used on the stream to have the screen divided like that (web-browser above, command line below)? Emacs? Vim?
   - I think it is several terminals and windows organized like that.  Current instructuor is using some tiling window manager, I think - check back later for details
   - It is recorded via Zoom (different meeting ID from the learner's Zoom). Only a portion oit is the browser with the lesson material and the bottom part is a terminal.

6. Will stashing be covered during this version control tutorial? I'd like to learn more about that.
   - The "Interrupted work" episode covers it, but we usually don't get to it.  (we used to, but it was often confusing in an initial course).  Check the exercises there

7. What are the differences between Git and GitHub?
	- git is a version control tool/format while github is a ommercial web service that uses it.  One option of many.
   - git is a program/method to organize/track changes while gitHub is the system where you can “apply”/ it
   - `git` is the version control tool and `GitHub` is (one of the) centralised collaborative platform(s) to share your git repositories. GitHub also provides other extra tools on top of git.

8. What is a git repository?
	- A git repository is a bit like an archive where different versions are tracked, i.e., like snapshots (called commits). However, the files aren’t just copy-pasted but only their differences are tracked.
	- Git history is the set of commits of the project. You can jump back to a previous commit and see the code exactly as it was at that point in time.

9.  What are problems with all the files??
	- Share/sync
	- You cant see the background of why a certain version exists.


14. How did you get to the annotation view in GitHub?
	- [here](https://github.com/achael/eht-imaging/blame/main/ehtim/imaging/starwarps.py)
	- Traditionally it is called blame/praise
	- if you are on the page of a code file on github, click on the `Blame` button
le, click on the""

15. Is git useful with overleaf latex?

	- Overleaf internally uses version control. If you decide to download your Overleaf project to your computer, you can make changes using git, then push it to Overleaf. However, you cannot use git in the browser version.
	- Otherwise, Latex + version control is a great idea, and many are using to write papers and theses.

17. What is the difference between github and gitlab? I le to get the annotation view in gitlab as well?
	- They are practically the same in basic features (like annotation view)
	- In my experience I've decided to use GitLab because I can set up restricted projects without the necessity of paying a fee. By this I mean that I can manage a project and select who to give visibility and accessibility to the project. At the time I started to use GitLab this option was not possible in GitHub. Perhaps nowadays it is. GitHub is more popular and was acquired by Microsoft some years ago. Nowadays, it works as a sort of Facebook oof code.

18. Should we repeat this process (git config) even though we did it before the workshop?
	- No (but it doesn't hurt)
	- You can check the `git config --list` and make sure it looks correct.


19. can I add diff.tool  to 'gvim -d' ?
	- Yes: https://stackoverflow.com/questions/26554865/how-can-i-make-git-difftool-to-use-gvim-gvimdiff
	- You can usaully make most editors work if you search around.

:::info
**Tip** To paste into nano, use ctrl + **shift** + V.
Also.. feel free to use your favourite editor.
:::


21. Is there an argument against using the desktop app over the terminal (as we do now?)
	- this is fine also but we start with terminal to have understanding of what is really happening but if you are comfortable with the app, it is ok to use it
	- And concepts from terminal help with desktop.  Most people need to use the terminal eventually.
	- Practising with the terminal is also the basis to write scripts and make workflows automatic
	- Working with the terminal is faster in terms of interaction with the computer peripherals (keyboard mouse video)

22. My bash prompt doesn't look nice, can I customize it?
	- As long as the terminal is a window within your desktop, it should have a menu bar with options to customize its appearance.
	- Here what I usually use. Paste this line inside your `.bashrc` file in the home folder
		- `export PS1="[\[\e[33m\]\H \[\e[32m\]\w\[\e[0m\]]\n[\[\e[31m\]\$?\[\e[0m\]] $"
	- There are million of flavors, some shell already have nice default setups like the "fish shell" https://fishshell.com/docs/current/fish_for_bash_users.html
	- Oh My Zsh can also be worth checking out https://ohmyz.sh/

23. I get the following warning in git bash:

	> warning: in the working copy of     'ingredients.txt', LF will be replaced by CRLF the next time Git touches it

	What does it mean?.

	- It goes about Carriage Return and Line Feed. It's the token use to mark the end of line, which may differ between Linux, Windows and Mac operating systems. Git is overriding the end of line of your text editor.
	- If you are using Windows, this will iron out things:
		> git config --global core.autocrlf true
	- If you are using Linux or MAC, this will iron out things:
		> git config --global core.autocrlf input



24. Where can I find .bashrc on windows for git bash?
	- Stack Overflow says `echo ~` might give you a hint.  `nano ~/.bashrc` might take you to the right place.


25. I still don't understand what "git add" is really for, or what it is doing, other than being required before "git commit"
	- Yeah!  It's basically some preparation, it splits selecting files and committing.  It may seem extra, but lets you check yourself.
	- `add` moves files into the staging area, `commit` turns the staged files into a snapshot
	- if you had only `commit`, you would either:
		- need to specify all files you want to add to the commit in that command
		- have loads of individual commits for each file you change
		- or you would only be able to ever do one huge commit with everything in the repository directory
	- You are not always keen to commit ALL the changes of the repository folder. For example, it is considered *bad practice* to add generated files. For example, let's say that you have a very light code that generates tons of data. You don't need to track the data, you only need to track the code that generates that data. In that case, with `add` you're saying "Next time I store my changes (`commit`), I only want to store the changes done to **this** file".
	  - That can also be done by not using the filenames with `git commit`.
	- Also, you don't have to put all of your changes to a file into one commit. You can commit only some lines from a file and then commit another set of lines from the same file with another commit message, for example.
	  - Can also be done with `git commit -p`
	- My thought: most of the justifications above can also be done with only `git commit` and the right options.  The actual advantage is *slowing you down* so you have a chance to inspect *before* you run the commit.  This lets you verify that your commit is going to be perfect.  Perfection isn't always required.

26. After `git init` + `git status`, I got a message "fatal: unsafe repository ('../recipe' is owned by someone else) To add an exception for this directory, call: git config --global --add safe.directory '../recipe/' ". Why does this appear?
	- Weird!  This is new to me.  Are you using multiple user acconuts, or user account + admin account, somehow?  Is this an own laptop?
	- this seems to be a new thing: https://stackoverflow.com/a/71941707

27. How do i edit one of the text files ingredients.txt or instructions.txt (i am using visual studio code)
	- Can you edit using vscode like normal file?
	- in terminal: `vscode ingredients.txt`


:::info
## Exercise until xx:40
https://coderefinery.github.io/git-intro/basics/#exercise-record-changes
Try to do at least Basic-1
All optional and bonus are extra
:::

28. I have signed up for this course via VU, but have not been invited for zoom sessions nor have i received the link to this file. Is there a zoom I can join?
	- They have their own zoom (?), maybe try contacting the organizer and check?
	- email to support@coderefinery.org
	- Hi, we have sent the mail last week, we can resend the mail or please reach out to us.
	- Problem solved!

29. I tried the `opendiff` and get an error message
	Launch 'opendiff' [Y/n]? Y
	xcode-select: error: tool 'opendiff' requires Xcode, but active developer directory '/Library/Developer/CommandLineTools' is a command line tools instance
	I should have xcode installed.
	- See https://github.com/nodejs/node-gyp/issues/569.
			1. Install Xcode (skip this step if you already have Xcode).
			2. Run `sudo xcode-select -s /Applications/Xcode.app/Contents/Developer`
	- Did it work??

30. about git diff. I entered these
	```
	bash-3.2$ git log --oneline
	5bb254f (HEAD -> master) added enjoy!
	496d216 add half an onion
	05828cf adding ingredients and instructions
	bash-3.2$ git diff 5bb254f 496d216
	diff --git a/instructions.txt b/instructions.txt
	index f7dd63a..6a8b2af 100644
	--- a/instructions.txt
	+++ b/instructions.txt
	@@ -3,4 +3,3 @@
	 * squeeze lime
	 * add salt
	 * and mix well
	-* enjoy!
	```
	I have a hard time typing here. Anyway, The hashes point to different files. So I see diffeerent results. Can you explain it?
	- Do you have different hashes to similar commits perhaps? That would be the expected behaviour.
	- For hard time typing in HackMD please copy and paste from another editor that you use as a clipboard. (I am doing this)
	- Those hashes point to `commits`, not files.  These commits point to all files, and when you diff them, it shows the diff of all changed files between them.

31. How do we copy paste hash codes in git bash
	- https://initialcommit.com/blog/how-to-paste-in-git-bash

32. I do `git difftool --tool=meld 4a6245a4fd` and nothing happens
	- It will not do anything unless you have uncommited changes. d try again.
	- Thanks it worked:smile:

33. can't exit
	```
	$ git difftool --tool=opendiff ingredients.txt

	Viewing (1/1): 'ingredients.txt'
	Launch 'opendiff' [Y/n]? y
	n
	^X
	:q
	```
	- `q` or close the window, if it is a separate window?
	- Solved.



34. I couldn’t do the git diff optional exercises. What should I put in the ``<hash>`` part?
	- Do `git log` first, which will list all the hashes of the previous commits. Use one of them, for example the latest one, to compare against. Another option is to use `HEAD` instead of the `<hash>`,  then you compare against the latest commit. If you still have problems please ask in Zoom in the next break.





35. I tried to Rename the file newfile.txt with git mv to oldfile.txt (you will need to git commit the rename) and recieved the message "pathspec 'oldfile.txt' did not match any file(s) known to git"
	- You didu do `git mv newfile.txt oldfile.txt` or the other way around?
	- I forgot to put git before the mv.

36. What does this mean in the output? "@@ -3,3 +3,4 @@"
	- The `-3,3` means "showing three lines starting from line number 3 in the first file", and `+3,4` means "showing four lines starting from line number 3 in       the second file".
	- start line and stride, in other words

37. What do you think about bulletpoints in a commit message?
	- I always use them!  Some don't.
	- I also think bullet points amakes es the commit more readable. Just keep the first line of the commit as an overall summary of the changes introduced in the commit.
	- Additional readings
		- https://cbea.ms/git-commit/


40. Instead of using .gitignore, can I do something opposite to this, I want to update?
	- This is sort of what `git add` does - you can add even if it is ignored.
	- you can put `*` in the top of your gitignore and then invert only those files you want to commit with `!` in front of the spec:
	  ```
	  *
	  !**/*.m
	  !*.m
	  ```
	  Should make anything that is not a `.m` file ignored by git
	- ah now I understand the question I think. it is indeed possible to list all the things that should not be ignored. I would still recommend to list things that should be ignored as this wil

41. How to remove large unwanted file from history?
	- (does not contain the answer) There is an optional section on editing history here: https://coderefinery.github.io/git-intro/recovering/
	- This is advanced. It will change the hash of every commit in history and make your branch incompatible with anything you have on a remote machine (such as GitHub or GitLab). You can run a command on each commit using `git-filter-branch`.  We would not recommend this unless you have experience or someone to help you, but it is very possible.
	  ```
	  git filter-branch --force --index-filter \
	  'git rm --cached --ignore-unmatch FILENAME' \
	  --prune-empty --tag-name-filter cat -- --all
	  ```
	  - push with `git push --force`

42. What is staging?
	- preparing for the next commit. the action of adding changes that will end up as the next commit - it gives you a chance to check and make sure everything is ready.
	- you can see it as putting your changes on a stage, for evidence, before you give your changes a time stamp and an explanation (with the commit)

43. If I have two repositories, how do I know which one I am initializing when I use git init command?
	- `git init` works on the directory you are currently in (by default).  It is unrelated to connecting to online repositories.
	- initializing is not related directly with an online repository. `git init` essentially turns the local folder you run it in into a repository. If you want to use an online repository, you can either `git clone` or set up a remote for your local repository.
	- keep in mind that repository can be either local or remote.  If you type `git help init` the explanation is
		> Create an empty Git repository or reinitialize an existing one


44. What does this signify? (HEAD -> master)
	- This will become clear later. However, master is the (sole, so far) branch you are on; and HEAD is a pointer that tells you where you are working. This is telling you that you are working on the default branch that you have at the beginning


45. Why `git rm` and `git mv` instead of just `rm` and `mv`
	- `git rm/mv` is the same as the `mv` followed by `git add` to tell git about it.
	- because with `git rm` and `git mv` you keep track of those changes (especially the move) which can otherwise get lost. Git sometimes tries to  notice that a file was renamed and not deleted and a new one created but you might loose a lot of history if it doesn't.
	  - Note: git doesn't track moves specially.  It looks at the files to see what was moved, so there should be no difference in history.
	- It is possible to move the file with `mv` but then you have to use `git add`.
	- If you use `mv` you will only rename the file in your directory, but Git does not do anything with that action. You should be able to see this state of the play with a new difference between your work and what Git knows, using `git status`

46. Can we use Microsoft Word as the editor?
	- Not advisable, because Word files are not in pure text format and contain a lot of encoded information about typesetting (formatting etc). Try to open a Word document with a text editor: this is what Git will see and track. The changes would not be intellegible, hence not meaningful.
	- Better use notepad (or a proper editor, like notepad++, which has syntax highliting)


## Continued: Branching and merging
https://coderefinery.github.io/git-intro/branches/

47. Useful alias: `git config --global alias.graph "log --all --graph --decorate --oneline"`
	- This way you only need to type `git graph` instead of `git log --all --graph --decorate --oneline`.


48. My HEAD points to the last action (file removal in optional exercise). Is that a problem, and can I move the HEAD again?
	- No problem if HEAD points to the tip of the master. `git log` should show: `HEAD -> master`. Or `HEAD -> main` if you use Windows or a different version of Git.

```
 $ git graph
		* e181d9d (HEAD -> master) File deleted.
		* 162d3f8 This is the renamed file.
		* 66361ef Extra file optional Basic-4
		* af1765f Extra fun.
		* 03a5671 add half an onion
		* 9f3a0b5 adding ingredients and instructions
```
	- All good!

49. What causes the difference between MAIN and MASTER?
	- In 2020, people decided `master` should be renamed because of associations with slavery.
	- Thus, we get this split thing where different git configurations have different defaults, many git installs are too old to change the default, and in the end we have these confusions and teaching is hard.
	 - :sweat_smile:! Thanks!
	 - when you create a repo on github, by default the branch is now "main"

50. You have a typo "comit" instead of "commit"
	- Is this in the materials or on the stream?
	- On the stream
	- OK, thanks!

51. How do I change the name from `master` to `main` ?
	- Changing by default for future projects: https://superuser.com/questions/1419613/change-git-init-default-branch-name
	- Changing for exaisting project: `git branch -m` (also may need to be changed in Github) (would recommend not doing this unless you can check what else may be wrong, e.g. if multiple people are working on it)

52. I have untracked files, are they always unaffected by my switching between main and branches? Or can they get deleted when I use "git checkout"?
	- They do not get deleted or changef if they don't exist in either the old or new branch. They will remain as untracked files in your working directory, recipe. If you type `git status` you'll get a message that untracked files are present.
	- They will cause issues if the new branch has that filename in it. In this instance, you will get a error, that your file is interfering with the branch you want to switch to.
	- Every time you check out a branch, Git will refresh the content of the working directory: it will take away and put files that it is aware of. If it sees that a file with a certain name is in the working directory unawares of Git, it will turn a blind eye to this, **unless** there is a name conflict with a tracked file. In other words, tracked files are moved around by Git; untracked one aren't.

53. How can I switch back to the branch master?
	- `git checkout master` or on newer git: `git switch master` (there is a note further down in material on why we still use the older commands so that it works for everybody)

54. When doesn't a merge create a commit?
	- It normally does, but...
	- ... If you are merging a commit that is strictly ahead of the current branch then git can "fast foward" and just move the branch pointer rather than creating a merge commit
	- see fast-forward (bottom of that page there is an example "Branch-2")
	- fast-forwarding is just linking a sequence of commits that did not "diverge" (you might have not needed to create a branch, in retrospect)


:::info
## Exercise until xx:00
https://coderefinery.github.io/git-intro/branches/#exercise-create-and-commit-to-branches

You should be able to make a branch and commits.  The goal is to have three branches at the end.  This will be used after the break - don't merge.

Poll: For the exercise, I am (multi-choice):
- done: ooooooooooooooooo
- need more time: o
- not trying: o
- it was too hard: o
- it was too easy: ooo:w
- o
- tried also optional exercises: oo
:::

55. How do I branch from M2 (a hash point different than the HEAD)?
	- step 1: `git checkout <hash-M2>`
	- step 2: `git branch <new-branch> master`; `git checkout <new-branch>`
	  - i don't think so, this will branch from master (but please try and verify)
		- instead: `git branch <new-branch> <hash-m2>` followed by `git checkout <new-branch>`
		- in one step: `git checkout -b <new-branch> <ha
			- It will not branch from master as long as you do step 1 first. But the `git checkout -b <new-branch> <hash-m2>` command is elegant.

56. Why do we see `experiment` still in the branches? Shouldn't it get "absorbed" by `main`?
	- Good question!  So, main absorbed experiment, but the branch still exists separately until deleted.
	- The way I remember: "merge will only affect the current branch".  In this case main, the other branch always still exists.

57. If I was on the branch less-salt and did a `git merge expermient`, those changes would get merged into less-salt? Should I avoid merging among branches and always just merge into main?
	- Usual workflow would me merging to main.
	- There are cases where you merge other branches - when it does what you want.
	- On larger projects, you commonly have a development branch, which is merged into and merges into master are only done after further revision of the development branch....

58. merge conflict: I get a conflict (see below) - how should i fix the conflict?
	```
	"$ git merge less-salt
	Auto-merging ingredients.txt
	CONFLICT (content): Merge conflict in ingredients.txt
	Automatic merge failed; fix conflicts and then commit the result."
	```
	- We will discuss resolving conflicts tomorrow.  I would wait for then to get details - we have a recovery plan.
	- You could try it on your own if you wish, following https://coderefinery.github.io/git-intro/conflicts/. You could `git merge --abort` to abort the merge that had conflicts and resolve the conflict tomorrow instead.

59. Do we have to define git graph again after we close the git bash?
	- No, it should stay as an alias in the configuration file `.gitconfig`, because we used `--global` flag to define it for all projects

60. Can she demonstrate how to use git diff to see what changes were made to ingredients.txt in master?
	- Sorry, it was missed. I recommend you check the recording, it should help you catch up.

61. Is it wise to merge with MASTER/MAIN and still work on in the sub-branch?
	- In some cases.  There is nothing wrong with it, so I would think "does this make sense / will I get confused?"
	- This is a good idea in paricular when working with several collaborators. If you have implemented changes in a branch that works (=is well tested) it is a good idea to merge early instead of waiting too long which may lead to lots of conflicts. This is also something that could be discussed / agreed upon with the collaborators.

62. Can we continue to edit in Experiment branch then? will it stays unmerged?
	- You can.  Some workflows do this strategy.
	- Interesting side note (on Github / Gitlab): If you continue pushing to a branch after you have opened a pull request, your new changes will be added to the pull request.
	- yes, new commits are added to the branch referenced by HEAD, whether the branch is merged or not

63. Very basic: How do I save my bash file?
	- Which bash file?  Your history?
	- Yes, I believe we have to upload this for a certificate in the end?
	- `history` will print out all history you can copy and paste.  See below also.

64. How do I save the work I did on the terminal today?
	- `history` will show all commands and you can copy and paste.  The file `~/.bash_history` should save it, though. zsh: permission denied: /Users/xxx/.bash_history
	- history only shows the last 10 commands or so :(
	   - try `history 1` (on my computer it shows then more since first command) GREAT! Thank you, that shows the whole history :)

## Feedback, day 1

:::info
See you tomorrow, same time!  Tell your friends, everyone is invited to come.
:::

Today was (choose all that apply):
- too fast: o
- just right speed: ooooooooooooo
- too slow: oooooooooooooo
- useful: ooooooooooooooooooooooooooo
- not useful:
- will improve my work: oooooooooooooooooooo
- livestream style was good: ooooooooooooooooooo
- would prefer in-person option:


One good thing about today:
- clear explanations ooooooooooo
- comprehensive overiew ooooooooo
- nice ressources oooooo
- easy to follow ooooooOnu
- when the terminal history of the instructor was shown.

One thing that should be improved next time:
- too fast type-alongs, but too slow other explanations (+3)
  - Thanks, good feedback!  (future days will pick up the speed)
- type-alongs weren't too fast for me, but sometimes I did not catch that this is a type along, because I just follow the terminal, so maybe stating it a bit more clear would be nice (+1)
- explain coding-terms (e.g. hash), as not everyone has the background
- More clearly say what you type when its a type along. Then you dont need to read instructors terminal while writing yourself
- More optional content in the exercises
- Many people got confused how git "stored" your files, perhaps explaining a little bit more of how git works and what is it before getting hands-on.
- Also, many people got lost into `bash` and `nano` and got frustrated from it. Kinda distracted from what git **is**.
  - What about a pre-exercise to demonstrate and get some experience with these tools?
- It was really nice to have commands history, but it was not visible throughout the workshop - could you make sure that if you use it, it is on always when we do type-along?


Any other comments:
- Have Breakout rooms available from the beginning of the session +1
- Tip: make sure all unnecessary browser tabs are closed during live stream. Instructor had a tab with email open, which could be accidentally shared.
- Mute zoom from the beginning - there was sound from two streams at the same time
- There's many commands to do same things, great that you didn't use too many to overwhelm!
- would it be possible to give a general way how to approach the exercises in other editors (sort of: what do you need to find out)
- Enable Exercise Leaders to meet their group at the start of the day. Late arrivals can create a backlog difficult to catch up with during the exercise.
- Richard's microphone had too much noise after the first break.
