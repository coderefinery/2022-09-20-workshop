+++
template = "page-with-toc.html"
title = "Questions and notes from workshop day 4"
+++

## Icebreakers

### What tools do you use for writing code?
  - vscode: oooooooooooooooooooooooooooooooo
  - eclipse: ooo
  - vi: ooooooooooooo
  - spyder: oooooooooooo
  - jupyter: oooooooooooooooooooo
  - rstudio: ooooooo
  - matlab editor: ooooooooooo
  - IntelliJ: oo
  - Qt: o
  - gedit: oo
  - CodeBlocks: o
  - emacs: ooooo
  - atom: oooooooo
  - sublime: ooo
  - notepad: oo
  - ms word: oo
  - IDLE: oo
  - nano/pico: ooo
  - VisualStudio: {it's vscode above? (they are two different programs: https://code.visualstudio.com/, https://visualstudio.microsoft.com/)}
  - Notepad ++:ooo
  - PyCharm: ooo
  - Arduino IDE: o

A guide to editor selection:
![](https://notes.coderefinery.org/uploads/ac9eb2f2-9205-4ad5-81a8-6857e3e8f568.jpg  =350x)

### What tools do you use for debugging code?
  - puts(), print(), console.log(), System.out.println(), cout...(+8)
  - ...or running it again without any changes and somehow expecting different results (+1)
  - ...or **praying**, running it again without any changes and somehow expecting different results
  - printo
  - breakpoint()
  - print() ooooooooooo
  - strace
  - try, except(+print), assert oooooo
  - debugging mode (+5)
  - import 
  - pdb ; pdb.set_trace() or import IPython; IPython.embed() +1
  - ic() 
  - print(), pytest, Ipython, python -i,  
  - going for a walk and getting a coffee +6
  - having a nap +1
  - waking up at 3 am with the solution (+1 but a blessing in disguise)
  - Matlab debugging tool +1
  - Spyder :sunglasses: o
  - explaining the problem to a colleague/friend o
  - Pycharm debug mode and then running program over and over again through the breakpoints

### Are you already using Jupyter for some projects?
  - yes: oooooooooooooooooooo
  - no: oooooooooooooooooo
  
Check out our upcoming (livestreamed) course Python for Scientific Computing: https://scicomp.aalto.fi/training/scip/python-for-scicomp-2022/
  

### Other questions from yesterday

1. The environment.txt and .yml files we created yesterday contain more than just the version number of the package (e.g. `numpy=1.2.3 py310..`). What do the other numbers indicate?
    - This number is the specific build version. In your example, it is build for Python 3.10. Often, conda packages are build for different operating systems and Python versions. These numbers distinguish between them.
    - major release, minor version, build number
    - Ah alright, makes sense. Is it necessary? Or is there a command so these build versions are not provided in .txt and .yml?
    - Not necessary, but it locks down the specific version and build of the package. You can ommit the inclusion of the build info with the argument `--no-builds` in the environment export step. This _might_ make your environment usable on multiple OS.

2. What's the difference between `origin master` and `origin/master`?
   - `origin/master` is a branch on your computer which follows the remote `master` branch on `origin` (it's a view of what the branch on origin was last time git checked)
   - `origin master` is part of a command: `git pull origin master` or `git push origin master`
   - ... and both `origin` and `master` are arbitrary names that point to a remote repo and to a branch, respectively

3. Can you hear them talking?
      - Yes: oooo
      - No: o 

4. Would you recomend that we keep working in the code refinery conda environment after this course or is it recomended to create your own instead?
   - for each project: make its own environment with a known environment.yml just for that project.
       - ... and add it to the git repository so that it goes together with the project/code/notebook
   - for general work that's not part of a project: I might use the general (full) anaconda environment which has most of the common stuff.
       - that's cool, thank you! 

## [Jupyter](https://coderefinery.github.io/jupyter/#)

### [JupyterLab and notebok interface](https://coderefinery.github.io/jupyter/interface/)

5. Unrelated: how do you create a world map with color-coded states? See the Activity Inequality State section in the lesson.
   - Good question. I don't know, but I'd start by looking at the repository and you can see...
   - which language are you using for plotting usually?
       - ggplot2/R or Matplotlib/Python
   - one of the many libraries: https://altair-viz.github.io/gallery/index.html#maps
   - search for "choropleth map in <your fav tool/language>"
       - Thx

6. What is a codebase?
    - the entirety of your project code (and sometimes dependencies are also considered to be part of the codebase)
        - OK, I would not call it a base if it is what I do, but fine like this
            - the assumption is that you use your code as a base for future work
                - Thank you.

7. Jupyter is not starting when i type jupyter-lab in my git terminal and i dont get a link
   - Are you in the CodeRefinery conda environment?
       - How do i know?
         - if you are in a conda environment it should be listed at the beginning of the line in parenthesis `(environment) your/current/path$ _`
       - I don't have much time but it was the instructions here: https://coderefinery.github.io/installation/conda-environment/
       - type conda activate and then conda activate coderefinery

8. What is non linear code flow?
   - (I think this is what they were talking about) What happens if you run the cells in some random order?  Then, you won't remember the order and you can't get the same results
   - I think what they meant is that in a notebook it's typically linear (first this, then that, finally that). There is a clear order. But many programs that we use are not working in a linear way (example: my browser. I can click whereever and I decide in which order it does things)

9. What is the difference between Jupyter Notebook and Jupyter Lab?
   - Notebook was the first thing made long ago: it was like "one notebook in one browser tab". It's still used sometimes but almost obsolete by now.
   - Lab was made a few years ago as the next generation, more like an entire development environment.  Probably recommended for most use.

10. I don't have the GitHub integration. Does something else need to be installed? +2
    - We might have removed that from the CodeRefinery conda environment for simplicity.  I don't think it matters for the lesson.
    - Okay!
    - It was because I wasn't using the CodeRefinery environment. Now I switched I have the Git integration.
      - excellent

11. I am using triton. Jupyter does not open in browser. Asks for some url. I am in the right env.
    - if you are not on your machine, you are starting a jupyterlab server on a different machine, and as such you would either need to connect to that machine, or you could use the existing jupyterhub on triton (jupyter.triton.aalto.fi)
        - Ok. started the jupyterhub. How can I start the notebook in my env of choice?
        - What I normally recommend doing is not starting Jupyter in an environment, but installing the jupyter *kernel* in the environment: https://scicomp.aalto.fi/triton/apps/jupyter/#installing-kernels-from-virtualenvs-or-anaconda-environments
            - This one works. Thanks
        - So you have the JupyterLab that is maintained by us, but you run your software in your own environment.
    - In general you can use SSH port forwarding, but it can be tricky to set up, especially if you are also using SLURM (then you need to also use the login node as a jump node)
      - Obviously nicer to use something supported by the people running the cluster computing facility 
    - How are you trying to start it?  Yourself, not through JupyterHub? If running yourself, this gives some hints (but that page is not updated recently): https://scicomp.aalto.fi/triton/apps/sjupyter/

12. Is VS code an IDE or a code editor?
    - IDE
    - VSCode is a code editor, but with the very extensive plugin system it can be turned into a full-fledged IDE


13. How can one achieve something like the matlab debugger in VS code when working with python scripts for example?
    - have a look here: https://code.visualstudio.com/docs/languages/python#_debugging
    
14. How to make Markdown as a default? it will change constantly to code view in jupyter-lab
    - give me a minute to find the configuration option for this
        - discussed here: https://stackoverflow.com/questions/40382454/jupyter-notebook-new-cell-type-default
    - but you can also use a keyboard shortcut to quickly toggle between code and markdown cells when in command mode: `y` for code and `m` for markdown
        - to go into command mode: `Esc` key

### [Exercise first notebook](https://coderefinery.github.io/jupyter/first-notebook/)
Task: Explore Jupyter some with the exercises on that page.

15. Error in the third cell: "zsh:1: unknown file attribute: h". Sorry, worked after switching to Markdown from Code.
    - Ah yeah, that makes sense.

16. how can one switch back and forth between seeing the actual markdown code and the preview?
    - Click / double click on the cell to go into edit mode.  "Run" to render.
        - thankx
            - also `Enter` to start editing the cell, and `Shift-Enter` to "execute"/render the markdown
    - Also: At the top of the file (in the menu part) there is a choose where you can set the type of the cell (Markdown, code, raw)

17. In the optional exercise, how do I make the kernel a conda environment if I donn't want to change the configuration of my computer?
    - you mean, install the other language without installing it system-wide?
        - Yes, exactly
        - Hm, I guess first is decide the language and figure out how to install it in conda.  R/julia are probably already there.
        - Then installing the kernel is probably the same.
            - Thanks!

### [Notebooks and version control](https://coderefinery.github.io/jupyter/version-control/#notebooks-and-version-control)

18. I see an ERROR in the jupyterlab-demo terminal: `[IPKernalApp] ERROR | No such comm target registered` and `WARNING | No such comm.` What does it mean?
    - That's completely new to me!  Does restarting the kernel help?
    - Nope, still the errors. Everything runs though.
    - hm, I guess if it seems to work, I'd ignore it for now.  If a problem, we can look after the course.
    - Okay! Thnx

19. JupyterLab is a JSON editor too, which is great. Any other suggestion about handy and pretty JSON editors?
    - I acknowledge the question but don't know!
    - Depends on what you want vscode does provide some features that make handling json a bit easier.
    
20. Is it possible to use Matlab code in JupyterLab?
    - There are MatLab "kernels", the interface between the web interface and the code.  So you can run the Matlab code from jupyter, yes (but the kernel is more basic than other languages)
    - Thanks

21. Is there a way to utilize React.js components in a jupyter notebook? As a widget, for instance to integrate interaction and visualizations?
    - Hm, I don't know details but I bet someone could write extensions that do this.  In only the user interface, I'm not sure.

22. Why jupiterlab, why not pycharm ? I see most of stuff is similar..
    - We used to have a lesson on IDEs in general, but in practice we need to choose something.  We thought that we could have more impact with Jupyter, since it's commonly used and advanced features are less known.

23. Is this a free service? Who is maintaining/paying for these online servers? 
    - Jupyter itself is open-source, you can run yourself (perhaps how most people do it). Or your organization can run (e.g. on our cluster)
    - having it hosted somewhere can cost something, but there are some providers (see next answer)
    - There are some free services like the MyBinder we will see later, that are funded by grants. Services like Google that host it for free somehow think it makes business sense to them.

24. **Too fast**: I missed how you do `git status` and then lost the rest
    - relayed.

25. how can i get the git extension?
    - It's in the CodeRefinery environment.

26. How did you open the terminal in JupyterLab?
    - From the left hand menu. There one open another Python session, a terminal, or other items. They will show up as tabs within JupyterLab.
    -  `Ctrl + Shift + L` opens a new launcher (also Menu bar > File > Open launcher). Then select terminal and drag it below.

27. My computer terminal is stuck after opening jupyter lab. How can I use it again?
    - Is JupyterLab still running? 
        - Yes
    - so while it is running, it's occupying the terminal.  I'd start a new terminal in parallel (but there are also ways you can run jupyterlab in the background so that it doesn't stay occupying the terminal)

28. I am using jupyter.triton.aalto.fi. How do I get the git extension?
    - I would need to install it.  I would have thought it is installed. Please make a Triton issue or com and I can take a look. 
      - Ok thanks
    - Looks like it works for me, at least I see the buttons there.
    - This probably means I need to discuss this in the garage

29. If you don't have the Github extension, can you use this terminal to push the file on Github?
    - Yes, everything can still be done in the terminal, and some people would prefer that. Basically it's up to you. `nbdime` also works from the command line.

30. What is the difference between `.gitignore` and `.git/exclude/info`?
    - `.gitignore` is kept under version control while `.git/info/exclude` is only locally kept. Use `.gitignore` for things that should be ignored generally in the project, like bytecode files, and `.git/info/exclude` for ignore specific things to your enviconment, like a `.vscode` file if you are using Visual Studio.

31. When I press the +- icon to perform the git diff, i get the error message: error loading notebook diff: file or directory does not exist: (filedirectory)
    - Strange... not sure what I can say without taking a closer look.

32. No color for me after enabling nbdime, but indeed no image code.
    - maybe you haven't made the change and saved it? I.e. so that the working version differs from the last committed version (HEAD)
    - modified /cells/5/source:
        ```
        @@ -8,4 +8,4 @@ for _ in range(num_points):
         hits += 1
         points.append((x, y, "red"))
         else:
        points.append((x, y, "blue"))

        points.append((x, y, "green"))
        ```
    - But no color. Not a big deal, I'll check it later

33. Feedback. This was difficult: one tab for the tv, one for JupyterLab, one for the lesson (the snippets) and one for the collaborative markdown... A lot of juggling.
    - sorry about that, hopefully it all makes sense after going through the steps after the workshop

34. Is it actually a good idea to commit results of each cell? Isn't it better to keep only formula/code and skip results. How to achieve this (keep only source)?
    - Good question! It depends, maybe you want the results to be available on Github or wherever.
    - For the case where you don't want the output (to make the version control more clean), there is `nbstripout` that can be used as a git hook: https://pypi.org/project/nbstripout/

35. I didn't get any differences when checking the changed file, even though I changed num_points and color. I can see the clear difference between the main and the changed files, but not in the diff view.
    - do you get any output from `git diff` in terminal?

36. I am getting "zsh: command not found: nbdime"
    - I guess nbdime isn't installed.  Are you using and have activated the CodeRefinery conda environment? got it, thanks
    - Someone just brought up the point "install nbdime hooks with --global in conda environment, but try to use it outside".  It depends on how it is installed.

### [Sharing notebooks](https://coderefinery.github.io/jupyter/sharing/)

37. If I am using a conda environment for my notebok, can I use a `.yml` instead of `requirements.txt` for binder?
    - Yes!  MyBinder can use standard dependency lists for many different languages: https://mybinder.readthedocs.io/en/latest/using/config_files.html
        - Thank you!

38. Is there some automated way how to find the dependencies / create the txt file?
    - In the general case, not really, unfortunately.  I usually start with what I think and test and add requirements as needed.
    - If you made a new conda environment for this, `conda env export --from-history` will show you what all you have explicitely requested in the past 
        - I think as of now, this only works with conda installed packages, so if you pip install a package into the conda environment, this is not exported . However there are efforts to include this and a PR is ready to be merged to handle this as well... 

39. Can you bind your project (notebook, whatever) to Binder directly from your local repo and not from GitHub?
    - Binder needs a way to access the files, if it's only on your computer then it can't really work.  It can from various other sources, including an arbitary Git URL (e.g. put it on your own webspace).  Check the dropdown on the page.

40. Can I publish the local repo to GitHub from the Jupyter extension? (Also I don't remember how to do it in any way - apart from creating a repo in github then cloning it and then copying the local files there...)
    - Yes you can, but you will always first have to create a repo on github, either manually or via the github API (https://docs.github.com/en/rest), but commonly it's easier to just do it manually. you can then add the github repository as remote to your local git repo (`git remote add origin git@github.com/yourusername/yourrepo.git`) . 
        - There is something wrong with the comment, it returns usage: git remote add `[<options>] <name> <url>`
        - oops, I forgot `origin` in the command.
        - Thanks!!
     
### [Exercise sharing dynamic notebooks on Binder](https://coderefinery.github.io/jupyter/sharing/#sharing-dynamic-notebooks-on-binder)
Do what you can, there are optional exercises.  Nothing else relies on this.

I am:
- done:oo
- not trying: 
- wish for more time: oo (if only one student is lagging behind, there is no way one team can catch up)
- good exercise: o
- exercise needs improvement:

41. I run into problems generating the requirement.txt file. I don't want to export the builds (see #1), so I tried `conda list --export > requirements.txt --no-builds` and `conda list --no-builds --export > requirements.txt`. But Anaconda doesn't lknow the builds.
    - but in this case you can create the file manually with only the matplotlib dependency. That's the only package outside the standard library of python
    - Okay, but how would I do this normally then?
        - it does work for me to do `conda env export --no-builds` to create an environment.yml file, which also works to set up mybinder environment

42. Is there a way of saving the figures generated in the binder jupyter notebook to our computer? like using plt.figsave(aslkdjfa;lk) but pointing to our local computer?
    - I guess you would need to download it (from when it is saved on binderhub at first).

43. Does mybinder.org uses its own computational resources to reproduce my results? Or how does it work? What if my coded requires very large CPU/GPU hours?
    - Yes, it is running on hardware provided to this end. Mybinder is sponsored by Google Cloud, OVH, GESIS Notebooks and the Turing Institute and in addition private sponsors (crowd funding) so that it can be offered free of charge for normal use (not too heavy computing).
    - Related: For the same reason the computational resurces are limited, the size of data sets has contraints (mybinder has to host all the data that you're showcasing). For more details, see https://github.com/binder-examples/getting-data, but in brief: if your data set is a few megabytes, it can be included in the git repository. If your data is much larger, say gigabytes, mybinder may not be the right platform for your work.

44. If I delete a file in a local Git repo, how do I stage and commit this deletion so that later this change can be updated in GitHub?
    - `git rm FILENAME` or `git add DELETED_FILE` (will "add the deletion" to the staging area)

45. I am trying to create the requirements.txt file with nano, but when I open it I see already a list with all the packages, matplotlib as well.
    - So you had a requirements.txt file already? If you start from scratch in a new git repo, you can first add the ThrowDarts.ipynb and then manually add the requirements.txt file.

46. How do I transfer changes done in the notebook in binder back to github?
    - You could add the Gihub remote (or use it if it's already there) and push it.  But it's an cloud service without security guarantees so maybe you want to be careful about that
    - so overall, I'd say binder is best for viewing projects, but not modifying them.
    - Binder heavily recommends not including any secrets (usernames, passwords, API keys) in the gitrepo due to the security issues so this, in my opinion, covers also pushing back to the git repo.

47. If I upload my entire env.txt and executed jupyter files, then others still can see the reproduction process. Could you be so kind to explain the additional benefits of using services like mybinder.org? This is related to Question 43, when the computational cost is high.
    - the benefit is the openness and reproducibility, but I guess it's less useful for computationally demanding notebooks. 
    - a good use case is to do this for supplementary information with published articles

48. I get this error when clicking the "laun h binder" button on github, so binder cannot open my notebook: "Double check your URL. GitHub recently changed default branches from "master" to "main". Did you mean the "master" branch?" Any ideas?
    - I got the same. +1
    - is the default branch in your repository named `master`? Maybe changing it to `main` will solve it.
    - New repository with main but again the same error. Working on win10

49. Could you add (later, no rush) solutions to the optional exercises of this section?
    - I'll add this as an issue on the repository! :+1:

50. My launch binder badge does not appear, even though I followed the steps. I have the README.me file with the code inside.
    - did you copy-paste the markdown text that looks something like: `[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/wikfeldt/my-jupyter-project/HEAD)
    - got the error. it's a .md file and not a .me :)


## [Documentation](https://coderefinery.github.io/documentation/)

### [Motivation and wishlist](https://coderefinery.github.io/documentation/wishlist/#motivation-and-wishlist)

Discussion:
Is project documentation important? Why?
- Yes, it explains how to run a program
- It helps the group to have a common understanding of the project idea
- Even if the function names are self-explanatory, you have to explain why the function is relevant to which plan
- Some people will read the code without knowing the language (as fluently as you do). This includes your future self.
- It helps to remember how the code works for me personally as well, for example, which units I have used.
- To check my previous work and decisions on data analysis. To share work with students/ collegues.
- Not even you in a month would know what the code does. Not documenting a project is equivalent to transforming it in a dream: you'll only remember things in detail 15 min after you wake up. After that, it is no man's land.
 
How would you describe a useful documentation?
- Clear, to the point. Not too much clutter.
- The minimum requirements: Installation, basic usage and description of parameters/arguments.
- Concise
- A clear table of contents and introduction.
- Explaining the meaning of any new variables, terms, libraries and files used.
- Not sure if it needs to be in documentation, but maybe citations for the formulas in given functions (or a short explanation of how the formula is obtained, it it  has been heavily optimised).

How can you motivate your colleagues to contribute to the documentation?
- It is hard. In my friends' opinion, one does not want to write the documentation for ugly code, and elegent code is self-explaintory. Another person I know says that lack of documentation keeps his/her job because only he/she could understand what the code does.
- It's the last 5% of the work that nobody ever wants to do. I am not even sure how I can motivate myself
    - Is it only 5 % though? I feel like the documentation should take as much time as writing the code. Depends I guess but still.
        - An ideal coding process of something somewhat complex should go as: pseudocoding, documenting, filling the empty spaces with the code. If you know what something needs to do and how it will do it, coding takes the least amount of time, most coding problems come from having to think what do you want to do and how you will do it *while you're coding*.
- Erradicate ducktyping
    - whats ducktyping?
        - https://en.wikipedia.org/wiki/Duck_typing :smile:
        - But this typing is about types and classes, not about typing as editing a document. Is this still relevant? Unclear to me.
        - Type annotations can help with generating API docs
- Show them non-documented code and ask them to write something useful, I've been cured that way.

Checklist: What do we want in good documentation?
- If there are only a few use cases "closed usage" examples are most important
- Readme; software requirements; in-code markdown; known issues; contact details.
- If there are many use cases "open usage" more is needed - motivation, topical guides and API documentation
- Visual representation of code structure
- Multi-language versions
- Standardization, like I can easily understand the content without puzzling what is meant, that we speak all a similar "language" to document
    - I would not want to enforce a "general" documentation standard. But within a project it makes absolute sense.
- Developer docs: how to get started, coding style    
- Description of parameters/inputs
- Wiki vs in-repository (tracked with git)?

50. What's your take on inline commenting of code?
    - (almost) Always needed, but not enough for users. Do I expect people other than me to use the program?
    - also here the "why" often more interesting than the "what"

### [Popular tools and solutions](https://coderefinery.github.io/documentation/tools/)

### READMEs

### [Sphinx](https://coderefinery.github.io/documentation/sphinx/)

51. I am getting this error eventhough I have the documents in the toctree: `WARNING: toctree contains reference to nonexisting document ' feature-a'`
    - the space in front of it is interesting. is there an indentation error?
    - see also 59

52. https://coderefinery.github.io/installation/python/#installing-required-packages link not working
    - where is it linked from?
    - aha found it. fixing ...
      - https://github.com/coderefinery/documentation/pull/245 
    - After Test Sphinx tool installation

53. Im not seeing index file
 - yes it seems to be in source dir
     - that happens if you use source and build directory

54. youre going really fast if we should have time to type along!
    - i missed the source suffix-stuff
    - not needed (probably)

56. I couldn't follow as it's going really fast.
    - thanks for notifying

57. I messed up a bit when it asked me the questions and I don't have now all these files. Can I do something about it?
    - maybe simplest is to remove all files and do it again?
        - I don't know how to do that. I tried using git rm but it didn't work.
          - git rm, only works for git tracked files. none of the files `sphinx-quickstart` created are under version control yet (you would need to add them first). So in this instance it would have been jsut `rm`. Also, is it possible that you selected the source/build repository option (as in #53)
          - I would go out of the "doc-example folder": `cd ..` and then create a new folder `mkdir another-doc-example` and try `sphinx-quickstart` again there. but maybe you are somewhere else on that page/exercise?
              - That worked, thanks!

### [Exercises sphinx](https://coderefinery.github.io/documentation/sphinx/)
Everything on this page, whichever you are interested in: 

I am:
done: oooooooooo
not trying: oo
wished for more time: oo

58. How do we get the nice theme that you are using for the course?
    - This is sphinx_rtd_theme: https://pypi.org/project/sphinx-rtd-theme/
    - It's the theme developed for https://readthedocs.org/

59. What is .rst?
    - "ReStructured Text": something similar to markdown but slightly more structure and some more options.

60. When editing the index.rst file Emacs tried to force an indent level for the 'feature-a.md'-line that is not what it is supposed to be for the build to work
    - is maybe question 51 related to this?
    - Yes I got the same error, but can one get past that in Emacs? 
      - there are now 3 spaces in front of the file name?
          - I got it to work with 3 spaces, yes, so I guess that works but I feel like I should be able to do it by tabbing somehow
    - Force the indent level, you should be able to make it indent right.  I can do it in emacs.

61. I can't get the image to work, I keep getting "WARNING: image file not readable: ..", no matter if I use absolute or relative path. It's a png and it does open otherwise: edit: sorry, my bad, dumb typo..
    - Hm... is the relative path relative to where the source is?
    - and "absolute path" is actually absolute path relative to the conf.py file (otherwise you can't relocate the repository).
    - in essence: All files that are supposed to be in your documentation or used by your doc need to be either available at some URL on the web, or need to be within the folder (or subfolders of the folder). My conda environment of coderefinery cannot be activated... 
    - what's the error message? (I assume the command you used is `conda activate coderefinery`)


63. The pros and cons are listed for various documentation tools, but not for Doxygen. What are the negative sides when using Doxygen? If it is all good, maybe the training could be offered for Doxygen in the future, instead of sphinx.
    - I personally don't see any except for a pretty strict requirement as to the style of the documentation.
    - Indeed nothing wrong with that tool and the reason why we focus on sphinx and markdown/rst in this lesson and not on doxygen is that sphinx is more general. doxygen is mainly used in the C++ community although it can be used and is also somewhat used in other languages.
    - Doxygen is mainly intended for API documentation. So it's only one part of documentation
      - one can also create "normal" documentation but I agree with you that API documentation is the focus of it and it is really good at that
    - Sphinx can also extract docstrings and type annotations at make time, though
      
64. What is the difference between Sphinx and Markdown?
    - Markdown is the file format. Sphinx the tool to convert it into nice looking formats (like html or pdf)

65. When I open the conf.py file I don't have the lines that we are supposed to replace. Is that a problem?
    - which line were you searching in there in particular?
        - I am sorry, this one: extensions = [ ]
               - I am checking on my side how it looks but it could be that it is not there and you can add it. just a sec ...
               - interesting that it is not there but can you try to add it? I just created a new conf.py and it was there.
    - Add the line, if it's not there already nothing to replace.  I guess the default conf.py of different sphinx versions is changing?
        - Does it matter where I put it? the order in the file I mean.
           - no it should not matter where exactly

66. How is the correct way to use this new html as a documentation in github? what shoud we upload and where?
     - after the break ...

67. I hope the name of the cat is Sphinx <3
    - oooh nice one!  Unfortunately not.  The stream name is "CATS" (who gets the reference?)

68. Why Sphinx/html instead of a simple tex or even word document?
    - word document: does not easily integrate with git
    - tex: is fine but then you need to render with latex/pdflatex and that can be done but requires a bit more installing and setting up but it can work. also markdown is easier to learn than tex (I really like tex)
   
69. To what extent would you use docstrings? Would you aim to have docstrings for all functions you define in your code? 
    - I would start with the functions that are visible/callable from the outside. the interface functions. it's less important for the functions deep down in your code that are only called by your code.
    - Ahh, okay, so maybe instead make sure to do inline commenting for those

70. I feel like there is some way to integrate docstrings you write along when you code with your Sphinx auto generated documentation, is this correct? 
    - Correct: https://www.sphinx-doc.org/en/master/man/sphinx-apidoc.html
    - It can be slightly more complex than other solutions if you want, but provides more control if you want.  Basic use can be simple still.
    - Can you mention other solutions? 

### [Deploying Sphinx documentation to Github Pages](https://coderefinery.github.io/documentation/gh_workflow/)

71. you are atill screen sharing the hackMD site
    - but better now? or still? 
        - for me, still
          - maybe reload the twitch tab? fixed, thanks
        - for me not :D
            - try and empty the cache of your browser

72. I can't hear him. Is it only me? Let's do a poll:
    - works for me: oooo
    - doesn't work:
    Ok I guess it is only me, thanks!

73. I don't have a folder `.github`. Is that normal?
    - maybe we should add it to the repo but currently it seems the exercise is to create it

74. FYI: `workflow_dispatch` is needed to run the action manually on GitHub (without needing a trigger). Button can be found here: https://docs.github.com/en/actions/managing-workflow-runs/manually-running-a-workflow
    - nice. TIL
        - TIL means ... "today I learned", sorry

75. Can we combine Sphinx and Jupyter, or are these two separate approaches to publish a code and its documentation?
    - sphinx can contain jupyter notebooks

76. For me it is `https://<username>.github.io/word-count/`
    - thanks this is the correct one
    
78. I guess this is of interest if your documentation is actually linked to your code (like question 70) otherwise there is no need to rebuild te documentation on a push since the documentation wouldn't change unless you have specifically rewritten the documentation, right? 
    - correct but maybe code documentation should always be linked to the code?

## Feedback

Today was:
- too fast: oooooooooooooo
- too slow: o
- just right: oooooo
- useful: ooooooooooooooo
- not so useful: 
- I would recommend it: oooooooooooo
- needs improvement to recommend: 
- just slightly too fast (last part)


One good thing about today:
- I am actually motivated now to write documentation, this was a great overview and "how to" 
- In general the learning about Sphinx (would have deserved more time, though)(+1)
- Binder! didn't think using it would be that easy...
- Getting an overview of tools that I had no idea they existed but will probably be useful for me at some point (if not right now)
- Nice guide on how to set up a reproducible and documented project code
- Jupyter is great, thanks for the introduction!

One thing to improve for next time:
- Provide a broad overview about what types of documentation exist (in-document, API, etc.) I had to google API documentation to find out what was meant (it turned out I knew what it was, I just didn't know the name). +2
- I would like some more details in the steps of yesterday's and today's material in the website.
- more about good documentation practice please (yes it's subjective, but at least we would hear some opinions from competent people...)+1
- Like in a recipe, you should first declare the ingredients so that we are ready to fetch and use them; then you can catch up more easily if you get lost for a second.
- Give us newbies a little heads-up on starting requirements (environment, directory etc)(+1)
- The Sphinx and working a documentation could be a whole day
- Maybe you can make a poll before the workshops about which are the topics that most people want to learn. For me, Jupyter notebooks was something that I already knew and it took away time for other things, while I would like to learn Snakemake much better. So for me take time away from jupyter and yield it to Snakemake, but for other people may be different.
- This was difficult: one tab for the tv, one for JupyterLab, one for the lesson (the snippets) and one for the collaborative markdown... A lot of juggling.

How are you attending?  (in-person, in a small group, watching at work alone, watching at home alone, etc):
- watching at home alone ooooooooooo
- in a small group in Zoom +1
- group at university ooooo
- watching at work alone oooo
- working at home with a small university group in Zoom o

How would you want to attend (and why)?
- I would prefer to attend in person (because of the social aspect of it and because I think it is easier for you to teach when you can get a feeling for the classroom), but I think the online format is working really well. Especially the hackMD option to comment and ask questions.+1

Other comments: 
- couldn't proceed with Sphinx but used the useful resources to investicate it and some alternatives for other languages.
- Felt there was enough time for exercises, but didnt really understand the talks. Like I had time to do the steps in exercises, but didn't get connection between talk and excercise. 
- would be nice to have repetition exercises so the people not familiar with the coding, environments etc. could get more used to the basics that you just run through.
- Is it possible to offer a small session to include cloud coumpting with all these?
    - do you mean teaching some about cloud computing here, or a way to use cloud computing to do tehse exercises?
- I am hitting information overload, but I also like that I learn about so many different topics. But keeping the focus with so many demos is getting harder.
- Without help from my zoom group I would have had a lot of trouble following. So I would definitely recommend this.
- Hoping for a workshop only focusing on sphinx and jupter notebooks and how to combine them! feels like there's so much to learn!
  - If at Aalto, let us know and we can arrange something.
- I think in general some of the most useful tips you provide are on best practice and what people usually do. In principle you could find guides etc for all the commands but getting to know the customs around code is more difficult to find on your own. 




:::warning
1. **Place your questions above this frame**, please.
2. **Funky markdown editor (this web page)?** If the crowd makes it hard to type in real time, try writing your question in a text editor and then copy and pasting it on the website 
3. **Number your question**, continuing from the previous section if applicable, please.
4. When you do not write, please **switch to "view mode"** by clicking the eye icon :eye: on the top left of this webpage.
HedgeDoc can feel slow if more than 100 participants are editing at the same time.

Thank you in advance!
:::