+++
template = "page-with-toc.html"
title = "Questions and notes from workshop day 4"
+++

## Icebreakers

### Icebreaker question #1
Computer programs are expected to produce the same output for the same inputs. Is that always true for research software? Can you give some examples?
- I have experienced often that different compilers or different compiler optimization levels produce binaries which produce different outputs. Most of the time it was the program that was not written in a robust way and not the compiler.
- Differences in outputs due to different architectures and therefore different slightly different numerical values, i.e. numerical instanbilities.
- It should. Reproducibility is the base of scientific research. Different environments can have different package versions, or different architectures can give different floating point approximations. For this, better to use a container or something similar to reduce variability.
- There would be a bug if the same input gives different output (or at least a feature change).
- Some randomization sometimes is used, but in general it is difficult to know the input of programs in my field, so most of the time I'm using the output to reverse-engineer the input.
- Does not happen always. If I change number of nodes/cores in parallel computing. If the software version is changed. Things change a bit even when the computer is changed. But all these changes have always been insignificant in my research though.
- Seeding random numbers can be challenging (not impossible) for really parallel/distributed programs.
- Some processes are deliberately random, yet we would like similar results for different seeds, e.g. training a neural network.
- Molecular dynamics simulations rarely do.
-  I think it depends on *what exactly* are you researching. If one would like to research for example people's reactions to different kind of random output, you would need a special research program, which would produce surprising answers to human input. Then the human reactive input would need to be recorded well. Could be some kind of a psychological study setting.
- I use randomization imputation in modelling which does not give the exact same output.
- I would rephrase the statement on top as just *the computer programs are expected to carry out the same operations* and the computers carry out *the compiled versions of the computer programs* -- so many weird things look more normal, that is  forewarned is forearmed.
- Monte carlo simulation with a same random seed at first should lead to the same result if all the random number generated are the same in every process.

### Icebreaker question #2
What do you want to be when you grow up?
- A composer and a sailor. Or a researcher.
- Gardener
- To grow more??? No, thanks...
- I want to be someone who never grows up.
- A systems developer or web developer
- Scientist :)
- I don't really care as long as I work with a computer.
- Astronaut
- Rich
- Paleontologist
- Astrophysicist
- Just growing up would be enough
- Mid-Term goal, embedded software/robotics (in the very broad point of view) engineer knowledgeable in Machine Learning, Optimization, system's dynamics, etc. Long-Term, project leader, preferable in academia. I want to take as much responsibility as I can and organize and keep a team efficient and make people's lives to feel purposeful and oriented.
- Possibly a user experience and user interface designer, maybe work with video games :O
- Founder of a unicorn company

### Poll: Do you start this week or did you already attend last week?

Started this week:
Also did attend last week: oooooooooooooooooooooooooooooooooooooooooo

## [Reproducible research](https://coderefinery.github.io/reproducible-research/)

1. I have a question about last weeks material. When can I just use `git push` and when do I have to add `<remote-name>] [<branch>:<branch>`?
    - To use `git push` your remote has to be set up (i.e. `--set-upstream` has to be executed once), otherwise you will have to define which remote/branch you are pushing to.
    - It also depends a bit on how you have configured git. Many people like to configure git to only push the current branch. Some people like to push all branches. Personally, I prefer to type it out since then I know what is happening, no surprises. I don't push more often than 2-3 times a day so it's not that much typing either.
      - In your .gitconfig you can look for `[push]` (if defined) on how it is configured. In my case: `default = simple`

2. Will we talk about licenses at some point? We have a model published, and we want it to be openly available to the community. But we want to avoid someone taking it, editing it, and then *not* sharing it.
   - We will talk about licensing and copyright later today.
     - cool, thanks!

3. Can you share the web you were showing? (practical info and such)
  - https://github.com/coderefinery/workshop-intro/blob/master/livestream.md

4. What is the difference between the commands `git pull origin master` and `git merge master`. If you're in branch master and you want to update your master branch with updates on GitHub (both were provided in the previous class).
   - Git pull can be seen as a combination of git fetch (download all commits that I don't have yet on my harddrive) followed by git merge. A git pull always contains a git merge. Instead of `git pull origin master` you could also do: `git fetch master` and followed by `git merge origin/master`. did this answer make sense?
     - Totally, thanks!

5. Do you make a distinction between **reproducible** and **replicable**?
   - Yes. One distinction is the one used in the figure displayed just now on the stream.
   - https://coderefinery.github.io/reproducible-research/_images/39-reproducible-replicable-robust-generalisable.jpg ![](https://coderefinery.github.io/reproducible-research/_images/39-reproducible-replicable-robust-generalisable.jpg)
   - But great question. Bood that you raised that there is a difference.

----
## [Motivation](https://coderefinery.github.io/reproducible-research/motivation/)
    
6. Not a question but I want to add to the motivation: I arrived to a group where the numerical code we are using was being share via usb stick. I have tried to convince my supervisors to use control version without any success. They disregard any attempt to make code re-usable and consider it a complete waste of time. It is almost impossible to me not to RAGE at this presentation due to the frustration accumulated. I've practically wasted my entire PhD time dealing with technicalities and being the only competent (or trying to become one) person dealing with the information systems and software. My PhD is finishing, I've no thesis or publications and my supervisors keep throwing that this is a lack of organization from my side. The situation is so unfair and the necessity of the PhD contract for me to live in a foreign country has made to me impossible to confront my supervisors.
    More than a question this is a reminder of HOW IMPORTANT is to write reproducible results and code that everyone can use. You're making people's lives simpler. Traceability, reproducibility and organization can save someone's career.
    *PD: sorry for the rant.*
    - You are not the first and will not be the least. I have a heart for your situation, but stand firm and tall. Do not compromise your integrity standards and turn your experience in a story of persistence, development and growth. *Sorry if this sounds patronizing, but I really know how it feels to deal with structural incompetence.* (OP: don't be sorry, this feels wholesome and all :) )
        - Our job carrier is also shaped by the bad experiences. There must be places where your values and skills are functional to success and not conducive to frustration.
    - thank you for sharing this experience. I am very sorry to hear.

---
## [Organizing your projects](https://coderefinery.github.io/reproducible-research/organizing-projects/)

7. I am using python. I have the main script/notebook and another script holding only functions that I call in the main. How should I structure the folder? In which folders should I save the functions and the main script?
    - (more about this on Thursday) First group related functions into common files. You can start with few files. Once files get very long and once it's difficult to describe by name what is inside a file, then it's perhaps time to split into two files. Give them descriptive names. These are then modules. They can all be in the same folder as the main script/notebook as a start. Once you start using the same modules in different scripts and notebooks, you can start collecting related modules into packages and then you create a subfolder with a descriptive name and move the files (modules) into the subfolder. After using this some more, you will become tired of copying them to different projects and keeping them in sync. At that point it might be time to create a package and package the subfolder and distribute it via PyPI or Conda (sorry for long answer but is this what you were after? Anything we can discuss in more detail or less detail? It's a process as a project grows)
        - Thanks for your answer! I am in the part where I am realizing that my functions are used in more than one project, but my question was more within a project, should I save my script `functions.py` in `src` (same as `main.py`), or should I create a folder at the same level as `src` called `bin` or something like that for the functions (I know I am mixing C and python structure but that is where I am confused :S)
          - It dependends partially on whether you want to make and install a Python package
              - Not for now
          - I would create a folder and move the related modules into it. Example: folder could be called `statistics` and the files inside could be called: `mean.py`, etc. Then inside `statistics` I would also create a file `__init__.py` which can describe the interface of the package. Then you almost already have a package which you can import into your main script and later also package on its own. In Python the subfolder often has the name of the package.
            - But, if this is not installed, then it can depend upon the working directory from which you start the script (I think?) (Or is it the directory of the importing script?)
                - Right now I have my scripts outside `src` and I have to make a trick like: 
                ```python
                import os, sys
                module_path = os.path.abspath(os.path.join('..', 'statistics'))
                if module_path not in sys.path:
                    sys.path.append(module_path)
                ```
	
8. Would you write a readme on how to get the data, maybe with a curl download command if applicable? Perhaps even as part of the evironment setup? Can this be generally audomated like when you install a package?
   - +1 for your idea
   - Data download can be automated and it might be a good idea.
   - Ideally both since data download scripts can break really fast.

9. How do I save the literature in an effective way?
    - I use EndNote to save and document literature that I ave used for research. University licenses exist for it!
        - Thanks for the suggestion
    - I use zotero is free and I think also open source and good ;)
    - Mendeley is a good tool. Good for maintaining bibtex files.

10. I think you have to pay for Overleaf git intergration now
    - Good point, thanks.
    - oh

11. Is this a write/code-along?
    - Not right now. We will soon have the first exercise for the day.

12. **Polite request to instructors**: please do not scroll up and down so quickly, pick up a place, and comment it. Your playing with the mouse wheel is visually annoying.
     - thanks

---
## [Recording dependencies](https://coderefinery.github.io/reproducible-research)

13. Explainer: [superfund site](https://www.thefreedictionary.com/Superfund+site)

14. Python has tools specifically shaped for dependency traceability. What about other less *academia* oriented languages such as C/C++ ? Can that be discussed?
     - You mean dependencies? (sorry I was distracted and not sure what you mean by "this")
     - There is a list in the bottom, we will briefly discuss.
     - C/C++ is not just for academia though; probably it has been superseded by Matlab in that role :-)

### [Discussion](https://coderefinery.github.io/reproducible-research/dependencies/#exercise-different-solutions-to-specify-requirements)

A:
- The most common case and worst since it is doomed to fail over time
- It's like saying "I don't care"

B:
- I don't understand the writing `git+https`
   - this can fetch the package directly from github (useful for development where you want to test it before putting it on PyPI or CondaForge or similar)
       - which syntax is that?

C:
- This look too narrowed with the specific version but maybe useful if an important feature for the project changes with the version (?). 
- I think this is the most easily trackable/able to reproduce
- Are `==` essential? As opposed to a single `=`
  - yes, for requirements.txt
      - who imposes this requirement to `requirements.txt`?
      - people who defined the syntax
      - See below https://coderefinery.github.io/reproducible-research/dependencies/#pip-and-pypi It's python-like.

D:
- .


14. If I have an existing project that is running, is there one command to get all the dependencies? So I know them and can put them into a file?
    - That depends a lot on the way you have set up the project. If you have been using e.g. a conda environment and installed everything via conda you can use `conda list`. Otherwise it's not that easy.

15. Can  PIP also have multiple environments like conda?
    - Do you mean: can we have with pip different environments on the same computer? Or something else?
      - If yes, then these are virtual environments and they work very similarly to conda environments and you can create as many as you like. Personally i create one per project and install everything into those and almost nothing system-wide. 
    - You can for sure have different 'pips' and name them f.e. pip2, pip3, dependent on your python version.
    - `virtualenv` or `venv` is what you would use - they map to directories, not by names in some common place.  One directory = one environment.

16. What could/would you use for Matlab users instead of conda?
    - Many matlab dependences are associated to the matlab version you are using, so if you can fix the version then your environment is solved (more or less..). For example in HPC systems, you might be able to do `module load matlab/r2017a` to load a specific matlab version from the past. There are "matlab runtimes" i.e. executable interpreters where you can (re)run matlab code (even from the past) without the need of installing a specific version. More info at:  https://se.mathworks.com/products/compiler/matlab-runtime.html
    - You can try to use a similar specification file and clearly list your dependencies (i.e. which Matlab version you used, which toolboxes at which versions and so on), but I'm not aware of a similar package management system.

17. I often use **conda** for reproducibility. Often my exported enviorment (in form of .yml file) fails to load again. What can be reason? This has happend many times.
    - It is probably too exact. If it includes the build numbers it won't load on other operating system.
        - Isn't it important to have it this much exact? That's the purpose of environment, what should I do to avoid it?
            - For pure(?) exactness you would need containers
        - +1, Yes, but unfortunately *exact* includes things like which OS it is compiled for etc. Interesting how *exact* is the opposite of *reusable*, isn't it?
        - true! But I have tried with using exported env in similar OS ( from linux to Linux, Mac to Mac etc) and I failed both times. I failed definitely while doing Linux to Mac.
    - I often export and then clean it up some: one that is exact, and one that is the general requirements
    - `conda env export --from-history` might be interesting to look at, but is not as exact.
    - Conda compatibility across operating system is not that good if versions are too exact (an environment made with Linux, might not *resolve* on MS Windows)
        - never knew that! I will be careful. But, then what's the better method of providing requirements, if not Conda?
            - With a container you can fix the operating system and its version and it can be run over other operating systems (like a virtual machine running on top of your current computer).
                -Oh yes ! containers. thanks :) but I feel containers might be more complex to set up as compared conda env for a newbie using my code.
                - I agree, the more *important* is a project, the more complex solutions should be used. If you are working on a clinical trial with thousands of patients, then you want to use a container. If you are doing a quick analysis for some project, conda is good enough.
        - I've had an issue, too, that an environment made on Windows doesn't work on Linux.
    - Depending on your code, you might actually want to provide two environment files, one "flexible" that should work on all OS, and allows to run your code, and one with precise settings that you used to create your results. That way you make the tool available to others while still allow best reproducibility options, but this will mean that you also need to provide OS/Architecture. 
        - I was also thinking this could be a solution. multiple envs for multiple OS.
          - I would prefer not to have one for each OS but one "general" and one "reproducing" environment.

18. Why would we use open source projects if **MATLAB** includes most of the tools that were explained in just one place? Plus is a verified language.
    - Because Matlab costs a lot of money and not everybody can afford a license.
    - Yypically yhis is not a problem when being affiliated to a university in the Nordics as all (?) pay for license or get a good deal but it becomes a problem once you leave and still want to use the code in your company/startup/free time.
    - Because matlab is owned by one person, there are fewer ways to do things. Maybe good because it is simple, but you quickly get to things you can't easily do.
    - There is no better verification than fully open source code and many eyes checking it. The same argument is also why R is better than SPSS which has had errors in implementation of statistical formulas in the past, and nobody could check the source code.
    - Because the next version of Matlab might disrupt your whole analysis pipeline by them deciding that they want to change something, or the next version is no longer compatible with an external dependency.

19. (considering the question above) My supervisors say that MATLAB is better because is payed and checked by *experts* when open source is just checked by *"amateurs"*. This is how we ended up with 50 K lines of code of MATLAB to run a project (obviously they are not the ones coding, so we are compelled to use MATLAB). Can more instructed people give me valid arguments against this?
    - Most very successful companies (like Google, Facebook, Microsoft), nowadays publish at least some part of their software in open source repositories, and, unlike closed source, you actually know what it does. Who protects you against matlab "phoning home" :alien: your code, it could even be disguised as some kind of license check or whatever, so this "closed source" usage can be quite dangerous.
        - My supervisors also told me that companies like Google, Facebook, etc, ask you to be **very** good at MATLAB if you want to work with them. Based on this answer, is this somewhat false?
            - I haven't seen Matlab as a required/requested skill for Google/fb. But I would need to check...
        - This is not true regarding MATLAB being required by companies. MATLAB has various issues as a programming language, so a MATLAB coder might need to unlearn some bad practices. Here a blog post that lists some of the issues: https://neuroplausible.com/matlab (I am Enrico Glerean, teaching Matlab at Aalto Scientific Computing and I am not recommending Matlab for skill transfers to industry :))
          - I think Matlab gets a bit too bad rep here. It is used by many companies on the interface between academia and industry because many decision makers come from academia and grew up with matlab and also because it is sometimes more expensive to rewrite existing code than to pay for license. It is a good language and can do a lot but the one downside is that it is not free.
                - (Enrico): I agree that because of the past of the decision makers Matlab still finds a way from Academia to Industry. In general (and I say this as a Matlab fan and teacher), there is no point in picking up Matlab since the Python ecosystem is fully mature, unless you really must use a tool that is only available in Matlab. Just type Matlab on linkedin jobs versus python (I did and it gives 98 jobs for Matlab and 1299 for Python in Finland, manually checking some matlab job offers also have python in the requirements).

20. What is the difference between **conda** and **mamba**? And which one to use?
    - mamba is a re-implemented conda that was made to be faster, using lessons learned form conda.
    - drop-in replacement

21. I always run into problems when I want to update Spyder, a package, etc. Conda simply doesn't want to update! I usually use pip update or follow instructions that Spyder tells me to use to update, but again, nope. Any advice?
    - My advice is that if you started with one environment and have all you need, then stick to that until the end of the project. If a major update happened during your project and you really need to update to newer versions, then make a new environment.

22. Why not Anaconda?
    - Good question. One advantage of conda vs Anaconda is that is smaller in size and number of files.
    - On shared computers (servers, supercomputers etc), one setup is to install globally different versions of Anaconda, and then have additional packages being managed by individual users by means of conda environments.
    - Anaconda is more convenient at the beginning since it provides most packages out of the box. However, in the long term we recommend to have a minimal base system and install packages into project-specific environments and for this, Miniconda is a better choice. For our workshops we therefore recommend Miniconda to prepare you for the long term and to start with good practices right from the start. Another benefit is the smaller install size and time. (quoted from https://coderefinery.github.io/installation/conda/)

23. What is the difference between conda environments and virtual environments? I thought they were the same thing. 

---
## [Recording computational steps](https://coderefinery.github.io/reproducible-research/workflow-management/)

### Exercise - [Using Snakemake](https://coderefinery.github.io/reproducible-research/workflow-management/#exercise-using-snakemake)

Use this time to plore the lesson and that exercise. We didn't do much introduction to give you time to explore yourself. Ask questions below and we will discuss at the end. This is the last *big* exercise of the day.

I am:
- done: oo
- not trying:
- need more time: JYU+5mins?

"talk less, give us more time".  I think:
- like it: oo
- don't like it:
- neutral: o (talk as much and give us some more time, because we rediscuss things after questions)
:::

23. For the exercise (in the preparation box), I want both the cloned repo, and another one using the word-count as a template? I'm confused.
    - You generate your copy from template on Github, and you'd clone your own repository. You can delete any old versions of the word-count repo now.

24. I noticed that when I use the coderefinery environment I installed according to the instructions, I get this:

    ```
    ==> WARNING: A newer version of conda exists. <==
    current version: 4.12.0
    latest version: 22.9.0
    ```
    Do I really have version 4? That sounds ancient.
    - You don't need to, I never do these suggested updates.  That does seem like a big version jump, though!
        - Really weird. I installed conda last week. `conda --version` also returns version 4 (this is on Mac), I will update it later today
        - The same for me. Installed last week (Windows 10).

25. Where can I find the syntax or beginner introduction to snakemake?
    - I guess somewhere from https://snakemake.github.io/

26. What does running a job actually mean? Is it updating a file to Github? or creating a record of a file being updated?
    - It runs locally on your computer. It makes some output files, and next time you run it can notice that the output files are already there and not run again.
        - What are the output files? Is that determined by the code in the repository?
    - A job in snakemake: is essentially one (parallel) execution of a currently possible step (like a worker in other contexts). Each step(rule) can be performed as many times as there are inputs for that rule. A job will take any currently available step (rule execution), where all conditions are met, and run it. This can be done in parallel, as long as the rules don't depend on multiple previous steps. But in our example, only the zip rule depends on all previous rules being finished. All other rules only depend on one file from the previous step, so if e.g. one of the books is huge, the other books can be counted and evaluated before that book's word count is done, and all *jobs* will in the end wait for this book before the zipping is done. 

27. Do we have to run the `snakemake --delete-all-output -j 1` command every time?
    - No.  Often, you would run without `--delete-all-output` and let snakemake figure out what you changed and only re-run the relevant bits.  There are plenty of other ways to control the output.

28. I get an error ModuleNotFoundError: No module named 'numpy'. It says "finished job 7", then "1 of 11 steps (9%) done".
    - this was part of the CodeRefinery conda environment - did you activate it, `conda activate coderefinery` ?
    - yes, I am in the coderefinery environment. I even see it in the conda list: numpy                     1.22.3          py310hed7ac4c_2    conda-forge
    - I wonder if one of the steps could be calling a Python command that is outside the environment.  I think it would be hard to debug without seeing it...
    - Could it be that the Conda update I've been runnning earlier messes things up? Anyone else having installed the update experiencing this?

29. I get ```bash: snakemake: command not found``` when trying to run ```snakemake --delete-all-output -j 1```. No worries. I had forgotten to set the conda environment...
    - +1

30. I am struggling a bit to see the purpose of snakemake. Can you comment on the difference between snakemake and just writing a Python program to check the directory for files and run the wordcount on that?
    - We'll discuss this in the wrap-up, good point, thanks!
    - It's really not needed everwhere. For something really simple, a script might be OK.  It starts to become more useful when you've got lots and lots of steps, they take a long time, and you need to be able to run certain bits.
        - great, thanks! :)
    - The usefulness stands out when you work on files that change in time (as for the number and size) and you have to replay the same workflow on it reliably.
One classical case is the compilation (=create executable binaries) of evolving source codes. But, it is not limited to that: you may have input files that get refreshed with some regularity, or you want to produce new output alongside old output (adding a single feature to an existing workflow, which grows).
Also, snakemake only reruns the rules (kind of blocks of a script) that involves files that have changed. You don't need to pick up what command you have to run once that file has changed.

31. Is snakemake only a Python thing?
    - It integrates with Python some, but you can have it call and run programs in any other language, too.  The "shell" lines can call any other programs.

32. I just want to add that I like the "talk less, give us more time" approach but I think a couple of more minutes explaining what snakemake is and why to use it would have been useful before the exercise to understand what we're doing in the exercise. +4
    - Thanks for raising this. It seems several participants have experienced the same thing.

---
## [Recording environments](https://coderefinery.github.io/reproducible-research/environments/)

33. I didn't manage to run Docker, even if installation was ok. Just the windows 10 can't anymore permit me to access the original BIOS to enable hardware virtualization.
    - I am not sure about your specific machine, but at least on Aalto Windows 10 laptop, it is enough to start docker as an administrator, I cannot check BIOS settings right now. It might be related to https://stackoverflow.com/questions/39684974/docker-for-windows-error-hardware-assisted-virtualization-and-data-execution-p
    - Thanks, using it as admin begin running and then gives the same error with this link https://docs.docker.com/desktop/windows/troubleshoot/#virtualization So it has to be the BIOS thing. I'll play a bit around it.
    - Hardware assisted virtualization and data execution protection must be enabled in the BIOS. The first solution didn't work either.
    - YES! It was a pain to get to the BIOS with the modern DisplayPort on a computer with real good old-style BIOS, but after succeding and enabling hardware virtualization Docker works now!

34. Issue. The link https://singularity.lbl.gov/ within https://coderefinery.github.io/reproducible-research/environments/#containers is obsolete apparently
    - Thanks for spotting this! Indeed Singularity is now Singularity/Apptainer. We will fix it.

35. Question in regards to Docker: Will the image know to update ones you already have it on your computer? Like, will I need to take any measures to make sure I have the latest version when running a Docker image?
    - The image will contain its own operating system so the version of your "normal" ("host") operating system is then less important when using the image. If I understood your question correctly.
        - Ah, sorry I think I worded it poorly. I was thinking if the image is updated on DockerHub. If I have run it previously on my computer will it know to run the latest update when I run it again after an update? If that makes more sense...
          - when you fetch an image from DockerHub then you indicate which version. Perhaps you take *latest*, and then it will fetch the latest at that time. If you then fetch *latest* few weeks later by e.g. building a derived image that refers to *latest*, it might then need to fetch a new version. If you refer to a specific version, then that one won't change anymore.
      - Ah thank you so much!
        - "latest" is convenient but is a moving target. good for development but maybe not ideal for reproducibility when sharing a container recipe for future generations.  
        - There are initiatives like the [Software Heritage](https://www.softwareheritage.org/) to preserve reliable versions of past softwares. I am unsure if right now they are already providing this as I have not used it myself.

36. Regarding the **dangers**, how can you find out whether a Docker repository is trusted? Say, I want an obsolete version of Ubuntu (to run programs not maintained any longer) and want to make sure it has not been tampered with.
    - There are some official suppliers for the different distributions, but yes, this is a general issue.
        - Is singularity any safer or does it invite more safety?

37. How about GUI programs? Can they go into a Docker or an Apptainer container?
    - yes

39. Is a docker comparable to a virtual machine? At least in my head they are similar things at this point.
    - Sort of similar, but the container uses the same *operating system kernel* so it is more connected to the host.
        - thank you!
    - Maybe is worth mentioning that Binder, continuous integration solutions and testing in the cloud are all based on containerized solutions. Containers are meant to also be destroyed and ephimeral, or replaceble. (Even Github services are running on containers). Compared to a Python environment, you can think of it as a fully computational environment (they are kind of virtual Linux machines)

40. Do you recommend Docker or Apptainer?
    - [Radovan] I use apptainer/singularity since I can use it also on clusters and I find it easier to use and learn and also use docker images. easier because I don't have to be root all the time, easier to remember command line options and the container image is a file and is easier for me to find, not forget, and move around
        - Thank you! I see.
    - From Docker images one can obtain Singularity images, so in that regard there is a smooth transition from one to the other

41. If Docker is so unfriendly, why not to explain Singularity if it scores better in any respect?
    - Good question. Docker is still vastly more popular so at least mentioning it was worth it so that we know what it is.
    - *Linux containers like Singularity cannot run natively on Windows or Mac because of basic incompatibilities with the host kernel.* You can however run a virtual linux machine and then run singularity on top of it... quite many levels of virtualization!  https://docs.sylabs.io/guides/3.0/user-guide/installation.html#install-on-windows-or-mac 
      - aha good point

---
## [Sharing code and data](https://coderefinery.github.io/reproducible-research/sharing/)

42. How do you combine FAIR principles with privacy laws? For me this is a big question in patient research. 
    - Assuming that the code does not contain hard-coded personal data (like patients IDs), then the code can be FAIR and made as open as possible. If you would like to attach some "demo" data to your open code, you can synthesize some fake patients. For example with tabular data https://github.com/DPBayes/twinify . Another alternative is to show a code demo with open data that has similar properties, and then those who will re-use your code will adapt it to their private data (and cite your code!).
    - True, however, not the data probably, unless you specifically ask this in informed consent. Example data is a good idea, thanks!

43. Does Zenodo also archive the git history?
    - Zenodo does not archive the whole git repo with the whole history
    - it makes a copy (archives) a snapshot but not its history

44. For every new release, I get a new DOI on Zenodo?
    - yes, exactly!
    - but Zenodo will also give you a DOI which will refer to the latest release and that can be used as well
    - Zenodo combines all version DOIs to an "umbrella" DOI, so you can use this DOI to cite all versions or refer to a software in general.

45. So, if I've written an analysis program for Matlab and I would like to share the code for the people who assess my thesis and the other scientific community to verify that I've actually used a clever automated program, would it be helpful to publish it in Zenodo and cite myself?
    - You could do so, however please keep in mind that what you put on Zenodo cannot be removed. So if your program is work in progress / not fully matured, it might be more suitable to share on e.g. Github.
        - indeed, I could just share my GitHub repo as a website. Thanks.
            - As a reviewer if I see only the github repo as a website I also ask for a snapshot to be uploaded to Aenodo. I have seen many repositories disappear while the Zenodo snapshot is still there. This can also be done after the peer-review process is over.
    - Yes absolutely (assuming license allows). We will talk about this in a short bit
    - If you need citations for your career, I recommend telling people to cite the paper that describes/used the code rather than citing zenodo DOI itself. This is a bit sad thing to recommend, but as long as h-index and other metrics are being used for career advancement, one needs to consider this. If you don't care about citations for your career, then cite the Zenodo repository.
    - Technically, Zenodo combines citations to single versions in a concept DOI, so your citation count does not get "fractured" and you can see the total number of citations to all versions on Zenodo.

---
### Wrap-up

46. Is there a reproducibility crisis also outside academia?
    - I think it is even more concerning outside academia, when software might be used to control cars or test new drugs.
    - ... although the legal and commercial stakes outside academia can be so high that it commands stricter quality criteria than in academia (where a lot of people can get away with lousy research provided they publish anything anywhere). +1

47. Can we actually trust Zenodo in the long run? Many services turn paid or disappear over time.
    - Zeonod is at CERN, so it should stay around for a bit.
        - I see, that's good. 
    - CERN has funding for at least the next 10 years +, which includes IT infrastructure. That includes funding and support for Zenodo.
    - See https://about.zenodo.org/infrastructure/ and sibling web pages

48. For a publication, how do I determine how many steps I need to take to make my code usable for others? (e.g. listing dependencies vs Docker vs something else)   
    - A good way is to ask a colleague/student/friend to install and run and get the same result as in your paper. this will often identify problems and is more practical than strict guidelines. see also https://www.reprohack.org/
    - Some universities are offering Research Software Engineers service, so they can try to install it and run it and help you publishing it (e.g. at Aalto University https://scicomp.aalto.fi/rse/)

49. Perhaps we can pool tips on common mistakes when coding towards reproducible scientific software (like the introduction of numerical errors from differences in rounding routines mentioned in the very beginning of todays lesson)?
    - Would be great! I am especially interested in the role of stochastic calculations and random numbers.
      - Good idea. We will touch on the topic of random numbers on Thursday within the lesson on software testing
    - Please also remember that some phenomena are inheringtely not-reproducible because of small effect size (= you need lots of data for detecting a small effect). So according to what you study you might struggle with irreproducibility independently from the code or quality of the data. There are solutions for these cases like "multiverse" analysis, "blind" analysis, but the best is the "multi labs" analysis where multiple research group collect and analyse data independently and then a meta-analysis is derived. Some writing about this https://www.aalto.fi/en/open-science-and-research/getting-started-with-reproducibility-in-research 

50. About reproducibility/reusability of code. I am confused between options. If a code (that does some data analysis for user having no idea of programming) is meant to be used by users later on, should it be written in langauge like Python etc, or data analysis work flows like KNIME etc? I feel users having no idea of programming would anyway not be able to contribute into code/data analysis work flow... wether it is s developed using a proper programming language or made using any data analytics platform  ...
    - This is a very good philosohical question.  It really depends on the case, but I think there is a real value in using a common language that people are likely to know.  Even if most users don't contribute, the few that do can be very important.
    - Think of the most basic unit that you want to be reusable: a Python function or the full pipeline? There will be more pipeline tools in the future, but they might still be able to integrate your Python function, so I would invest making the single unit more reusable, and wrappers/pipelines/etc will come and go.
    - I [name=rkdarst] realized this connected to the [KISS principle](https://en.wikipedia.org/wiki/KISS_principle).  I really liked this comment there: "with the challenge that the jet aircraft they were designing must be repairable by an average mechanic in the field under combat conditions with only these tools."  So how easy is it for you, or someone else, to fix it? (update: I'm not trying to say I know the solution, only that it was interesting to think about)
        
        - Then again (!) how do we define a "common mechanic", "common user"... who is more likely to be found easily in future if I am not there to help with pipeline/code? A python developer, or a data analysis work flow (e.g KNIME) expert to work on the code in future?
        - +1, it depends.  This is why software can be fun.
        - I usually try to define "is this project about getting something done (use simple tools) or learn something new (be more bold)". Both OK in different cases.

51. Is there a useful tool to generate a requirements.txt-file for an existing project?
    - `pip list` and `pip freeze` say what is installed, but everything - even dependencies of dependencies.  Often, making it by hand gets the highest-quality list: you know exactly what you need.

52. I'm still a bit confused with what Docker is doing. Is it somewhat the same process as when creating .ISO files of a CD? So it's creating an image of a program with the code that I want to be run... kind of... emulating the environment that I have been working on?
    - Imagine if that .ISO was a "Live CD" with the whole operating system. Slightly more like that, but more specialized.
        - thanks.

---
## [Social coding and open software](https://coderefinery.github.io/social-coding/)

### [part 1: Social coding](https://coderefinery.github.io/social-coding/social-coding/)

#### Question 1: Why would I want to share my scripts/code/data?

- A: Easier to find and reproduce (scientific reproducibility)
- B: More trustworthy: others can verify correctness and find and report bugs
- C: Enables others to build on top of your code (derivative work, provided the license allows it)
- D: Others can submit features/improvements
- E: Others can help fixing bugs
- F: Many tools and apps are free for open source, so no financial cost for this (GitHub, GitLab, Appveyor, Read the Docs)
- G: Good for your CV: you can show what you have built
- H: Discourages competitors. If others can't build on your work, they will make competing work
- I: When publicly shared, usually we timestamp or set a version, so it is easier to refer to a specific version
- J: You can reuse your own code later after change of job or affiliation

**Choose many**. Vote by adding an `o` character:
- A: ooooooooooooooooooooooo
- B: oooooooooooooooooo
- C: oooooooooo
- D: ooooooooo
- E: oooooooo
- F: ooooo
- G: ooooooooooooooo
- H: o
- I: ooo
- J: ooooooooooooo


#### Question 2: The most concerning thing for me, if I share my software now

-A: It will be scooped (stolen) by someone else.
-B: It will expose my "ugly code".
-C: Others may find bugs and mistakes. What if the algorithm is wrong?
-D: I will get too many questions, I do not have time for that.
-E: Losing control over the direction of the project
-F: Low quality copies will appear.
-G: I won't be able to sell this later. Someone else will make money from it.
-H: It is too early, I am just prototyping, I will write version to distribute later.
-I: Worried about licensing and legal matters, as they are very complicated.

**Choose one**. Vote by adding an `o` character:
- A: oooo
- B: oooooooooooooooooo
- C: oooooooo
- D: ooo
- E: ooooo
- F: oo
- G: ooo
- H: oooooooo
- I: oooooooooo


#### Question 3: Why is software often treated differently from papers?

Free-form answers:
- is it?
- Because researchers are often not knowledgeable enough to know how to properly treat software (or too scared to try)
- I work in theory, and sometimes people seem to look down on researchers who develop code rather than doing so-called real research
- Scientific orginality is hard to extract from a software 
- Most of scientists do not know how to properly cite or reference code and software. Just commercial software that specify how to be cited and provide an implementation to automatic citation software (or bibtex).
    - This can be addressed by adding a "How to cite" with a bibtex entry to your README, and yes making it easier for others is important.
    - One can include a citation to the Git repo / project website / Zenodo link in papers. Some journals only allow references to papers, when that is the case one can combine in the same reference item a reference to both a paper and to the code.
- It is traditionally considered to be a method, not a research output.
- For historic reasons maybe, papers are an older more establishedformat.
- The opportunity cost is high, i.e. if the software is so sucessful, then the developers or the sponsors may be more motivated to sell it as an commercial product, which is the opposite to let other researchers know every detail of your work.
- Software is often seen as something for *Software people* and relegated to work for technical people. Most of the code I've seen in research is *spaghetti* code that can do only one task in a very specific manner and only the author knows what it does, so, imposible to share and *experts* don't want to show how they work.
 - Software is developed continually. New features can be added to a software library such that the software library contains implementations of many algorithms. Publications (papers/articles) tend to be a "single unit" (just one main thing/idea) AND "single shot" (published only once and not revised significantly).
 - When I submitted a manuscript recently my superviser said that I should make my scripts public because that is good practice, but that I "shouldn't spend too much time on that because no one will look at them anyways", that culture makes me unmotivated to improve my practices
     - This will change immediately with the first reviewer that will look into the code :-) *Sorry I couldn't keep it*
- I am not trained to develop software/code in such a way that it can be shared and reused. This is one of the reasons for following this course. I am trained to write a report and publish it. 
- No one will give you a PostDoc or Professor position for your code used in research. The only thing that matters in academia is the number of **articles** you can produce.
    - I know some postdocs hired for their software skills.  Less likely for professors (but being good at software could get you more articles), but there are other career paths for research software engineers. 
    - Yeah, but they can be good at software but not good at sharing code. Same as professors can have 0 pedagogic skills but the university demands them to teach. I think there's not motivation for academic researchers to neither share how knowledge is built nor to make it reproducible, only results and final plots catch the eye (and this will keep like this if the only measure in an academic career keeps being the number of articles).
- You can get funding for your research/paper idea (again needs papers to prove idea and get funding), no funds for your software ideas if you are working in academia.
  - There are specific calls for grants for development and improvement of codes. For instance the EU center of excellence calls, see e.g. the [TREX](https://www.trex-coe.eu/) project that promotes the development of programs, libraries and workflows for theoretical quantum chemistry simulations.

#### Question 4: When you find a repository with code/library you would like to reuse, what are the things you look at to decide whether you use it?

Free-form answers:
- How easily I get it to run (If I need changes: also how easily I can understand what the code is doing, and how to edit it) +2
- I look into it first and see if I understand it (is the code clear, commented and documented)
- I check the licence requirements +1
- Community involved (number of pull requests submitted/accepted, issues resolved) - most probably problems will pop up, and only community can help. No community = no help :(
- Whether it's used by others as well. +1
- How quickly can I test some kind of "proof of concept" with the library?
- the coding ability of
- Repository activity (last update), number of stars/downloads, documentation (getting started) +1

#### Your Questions?
53. How would you advise if some incident hppen? I meant if I use faker.js but Marak, creator of faker.js who recently deleted the project?
    - It's always a concern.  My main strategy is to understand the risk and try to focus on large, community, open-source projects.  More contributers = less risk, and if the main developers go off, at least others are around who can help provide an alternative.
    - It seems that Faker project is fully copyright license (https://github.com/faker-js/faker/blob/main/LICENSE), I would be discouraged in using it as it locks my work especially if I think my code is important and should be re-usable in X years. For the same reason alternatives to Matlab and SPSS are recommended as then my code is not locked to their secrets.

54. Suggestion for another entry in Question 1: it invites me to code properly from the outset!  (And I know it will take it longer so I can budget time and manage expectation)
    - Thanks. I opened a pull request with this.

55. What about non-commerical licenses, which are somewhat common in some fields e.g. in computer vision?
    - It's an option, but limits the community that could contribute and wouldn't be included in open-source collections.  It won't become the next numpy.  Could be useful depending on your future goals.
    - My university's innovation people recommended the GPL license if you might want to commercialize later.  They said it rarely interfers.  [A]GPL license = others can reuse for anything, but any derivatives have to also be open.  It keeps your competitive advantage, since only you can make it closed later.
      - I guess this could be troublesome if you accept contributions without requiring copyright assignment.
      - As soon as you accept contributions from someone else, **from that inclusion onward you are bound to the LICENSE used unless all authors agree to a change...**
      - And GPL: I don't see how it keeps you competitive advantage, since anyone can do the same thing you do based on the GPL version. 

56. Does the code belong to the company or the person that codes? I think in this matter it is not different from manual labour in other areas, but the problem of coding is that code can slip from companies hands easier. Why the software belongs to the coder that works for a company when this is not a discussion in other fields?
    - Usually yes, a "work for hire" (by employees) is owned by the employer.  You should ask about open source policies - especially universities let you share.
        - Indeed, universities are employers and researchers are hired. 
          And universities run research projects that are confidential too. 
          So it is not just about "companies".
        - Then how do you showcase/prove your skills? If it belongs to company (non-academic setting), you can't take it with you when shifitng position.
            - A common way out I heard of is that you will be able to rewrite it. The new employer may want to hire for those skills. It is important to make sure that, when you leave a company, you don't undersign a prohibition to compete (which actually would push you out of the market you worked in that far).
            - Are not such prohibitions commonly time limited, to say 6 or 12 months?
                - Depends from case to case. Always mind what you undersign when you leave a company. Do not be distracted by vague notions as 'commonly'.
        - good question and yes this is a flaw!  Side projects, asking to open-source and share,... (any more ideas?)

57. Manuscripts can't be seen as "done" so strictly. One shouldn't base their new study on old manuscripts, at least not only on those. In my field (and I suppose other fields, too) it's important to cite the newest research. So it gets old, too.
    - The **definition of done** (please look it up) is one of the tenets of so-called agile programming, aka 'scrum'. I would dispute the myth of never-ending coding.
      - Software libraries do not exist in a vaccum. Integration with other software is the cause of bitrot. 
    - +1! And often old manuscripts are proved false and it takes lots of effort to unlearn what everyone thought was the "truth".
    - Practically speaking "the scientific method" is an algorithm, which is agreed upon and used by the academia. The research done builds on (hopefully) all the previous work, broadening the common knowledge. But the scientific method calls us to doubt even the latest publications.
    - This is the myth of standing on the shoulders of giants. Sometimes you need to triage how tall the giants were. These are the review articles.

58. My Github account is with my work email. If I change my organization, I loose that mail account. Is it advisable to use personal mails for github accounts?
    - I guess it depends on if all projects are owned by that organization (and its policies).  For me, I use personal email.  You can add multiple emails.
    - I have both a personal and the university email associated with the account. The university account can be exchanged if I change organisations...
    - Are you allowed by your terms of employment to fork the repository? If so, the problem of mail address appears to be secondary.

---
### [Licensing](https://coderefinery.github.io/social-coding/licensing/)

### Question 5: Which of these are derivative works?

- A. Download some code from a website and add on to it
- B. Download some code and use one of the functions in your code
- C. Changing code you got from somewhere
- D. Extending code you got from somewhere
- E. Completely rewriting code you got from somewhere
- F. Rewriting code to a different programming language
- G. Linking to libraries (static or dynamic), plug-ins, and drivers
- H. Clean room design (somebody explains you the code but you have never seen it)
- I. You read a paper, understand algorithm, write own code

**Choose many**. Vote by adding an `o` character:
- A: oooooooooooooooooooo
- B: oooooooooooooo
- C: ooooooooooooo
- D: oooooooooooooooooo
- E: oooooo
- F: oooooooooooooo
- G: ooooooooo
- H: o
- I: oo

#### Your Questions?
59. Answer I (write code from alg. one "understands"): cite the paper!

60. What does "clean room design" in answer H refer to?
    - One set of people looks at code and writes a specification "here is what it does".  Another set reads that specification and writes new code to do the same thing.  Main point is to specifically avoid making a derivative work.
        - Is it the same as writing pseudocode?
            - No, it's even more extreme than that. Pseudocode still has the creativity of the original authors, and that is the copyrightable part.
            - https://en.wikipedia.org/wiki/Clean_room_design 
            - Thanks
        

61. What if I only distribute a patch, and tell people to apply it themselves. Is it a derivate work?
    - The patch: you probably had to look at the orginal code and carefully make the patch to work with the code.  You could argue it is, or isn't.  These type of interfaces are a common debate/cause of legal action, but if you are small it's probably not a big deal in practice.

62. How to prove that my code is not a derivative work?
    - You can try to document how you make it, have good history, etc.  But in the end, for copyright it's a legal thing.  Lawers would argue in a court (and this is why big companies are much more strict with their projects).
    - Take note. There are specialized lawyers for screening these issues. Or law firms hire computer science firms for forensic work. (It's not a cheap affair.)

63. Is there such a thing as "plagiarism detection" software for code?
    - Yes, there are different tools that try to do this.
    - Git is a plagiarism detection software, in a manner of speaking :-) It checks if your successive commit plagiarises an existing commit. 
The shell command `diff` is an even older implementation of the same searching/chasing for existing content.

64. If I find a function that I want to use but the license is closed, what can I do? Can I somehow write my own version?
    - a) Use the function and you can never re-distribute or re-license your code
    - b) find another option
    - c) you can try to rewrite.  It would be a grey area, if you look too closely and follow the creative design of the original function, it would technically be a derivative work.  See discussion of clean-room design above.
    - d) make a study of the similar functions available to your community, review them (and publish the comparison, perhaps, if this has a general interest), and then create your best implementation.
    - e) you can contact the author also and suggest to distribute that part differently? this is perhaps more relevant for the many repositories without any license than for actually closed code.

65. Ownership: am I the owner of some code I wrote? Indepedently of the license I use.
    - Yes: license to others doesn't change ownership.  Owner can change license later, others can't.
    - If others contribute, they become co-owners.
    - Note "owner" for copyright only means "I have the right to tell others not to use it".  Subtle difference from "I can do anything I want"
    - Also: If you publish on an open source license, and later change the license, anyone who copied it while under the OSL can continue using it and distribute/modify it. 
    - **Copyright is not the same as authorship and ownership**. Copyright is about the right of multiplying and distributing a work; you may be the author, the owner but have forfaited your right to multiply and distributing it (for a fee, for a number of years, for example).

66. Hypothetical situation: I license my code with a **strong copyleft** license. I found someone uses it in a closed form. Politely: so what? What would happen?
    - You (the owner) would have take legal action if asking nicely doesnt' work.
    - Examples: https://en.wikipedia.org/wiki/BusyBox#GPL_lawsuits, https://en.wikipedia.org/wiki/Gpl-violations.org . Enforcement does happen!
    - It strongly depends on your jurisdiction, and how much legal expertise you can count on. And in which country where the infringement has been committed...  Downsides of the global village. 

67. What if a repository is licensed for "non-commercial" use. Can it be used for research (with code + article published)?
    - You would have to read the exact license but probably yes.  Though technically look at conditions and your organization, etc.
    - I am unsure about software, but data collected with public funding is by default licensed for any commerical use (EU open data act, assuming data can be reused e.g. no ethical or legal constraints). I would expect the same applies to software, but I would need to find a reference.
    - (I removed my comment on anaconda, I can't confirm it)
    - I guess it depends on the "business model" of your university.... +1 
        - Universities can have commercial branches/spin-offs, which may be smartly set up to exploit the loopholes in licenses and create profit. There must be some office/r on Intellectual Property that oversees this.

68. Where is the slideshow with the recipe and the licensing examples?
    - https://cicero.xyz/v3/remark/0.14.0/github.com/coderefinery/social-coding/main/licensing-and-cakes.md/ thanks

69. Can you comment briefly on the Creative Commons licenses?
    - Some very well-developd and standardized licenses for general data and artistic activities.  Not designed for code.
    - They did an especially good job of making four standard categories clear and explaining what they mean, which is very helpful.

70. It seems that the code development history can be easily fabricated. So somebody can just steal my code, add his/her fake history and claim ownership...
    - In that unfortunate case, you have your code history to debunk the plot. But, indeed, it is a conflict situation that has already fired up. 
    - You discourage the nasty by raising the bar of the criminal energy that s/he has to use to steal your work.
    - But people would look at time stamps. and they can be also modified. This is a great point and another reason why git history is so useful because recreating one very quickly is unlikely.

71. if I published code without a license, anyone can take it, edit it, and not publish it, if they get it before I add a license?
    - The default license is "no license", meaning they can't do anything.  But someone can use and not publish/tell anyone even if there is a license.
    - Interesting read for software without a license: https://en.wikipedia.org/wiki/License-free_software

72. If I'm writing code during my research work, can I write it under a open source license? What if my supervisors are against it? If I don't remember incorrectly, there's a point in the university contract that says that anything I produce related to my research work belongs to the university.
    - You would need to ask your university. If your supervisor doesn't want to, then that is probably a problem.  (unfortunately, universities say so much about open science, but then also make it so hard actually do it)
        - Yeah, unfortunately my supervisors don't want to share, but didn't participate either. So the group will inherit my code without posibility from my side to share it or show it to others, potentially hindering my possibilities to build a better CV for future employment.
            - This is very unfortunate! If you are at Aalto please get in touch with one of us as we could discuss this with your supervisor (but I also understand that you might not want to disclose this, and I am sorry) [Enrico]
            - It depends on the policy of the university, which is above your supervisor's whims. Check if there is an office you can inform yourself about this. 
            - Note that you do not loose employment opportunities by following the rules of your employers. You will have to explain your claims about your skills, which you have to do anyhow. You might have a slightly longer job interview, but not much more than that (if you deal with humans and not an automated recruitment/screening process...).
        - In Finland there are going to be policies for open software that would basically highly recommend for software to be open. Your supervisor might still have a saying that "software should be closed", but it would need to answer to university management why it is so. 
            - Same in the Netherlands. Not just the universities but also the State funding bodies.
        - Might be worth finding the "open science" people at your university and ask them for advice.+1

73. Will the Zenodo snapshot of GitHub survive if GitHub disappears overnight? Are the files *transferred* to Zenodo?
    - Yes, Zenodo makes a copy and the point is that it can survive Github disappearing.

74. If I use someone's code that is published under a GPL license, do I need to do anything other than adhering to that standard, when I publish code which is build on their code? Cite them in the README?
    - keep their copyright notice, add yours, and it helps users of the software if you also summarize how your version differs from theirs (if small modification). if a small GPL component was introduced, then I would describe that in the readme

75. If you have graphics in the repo for a GUI for instance, is that covered by the licenses you presented or should they have a CC license for instance? And how what that work with more licenses for one project?
    - you could say that code is distributed under license X and text and images shared under CC license Y.

76. Is there such a thing as licence hierarchy, in the sense: a project composed of different pieces of software each with their own license -- does the entire project fall under the "least permissive" license?
    - Typically license is per-project but it is possible to license per-file (MPL allows that).
    - If the components have permissive license, then they can be redistributed under a new/different per-project license. If a component has a strong share-alike license, it might "infect" (not a very nice word but sometimes use) or overpower the other licenses

77. Can I publish a repository with files generated / used by a commercial software?
    - An excellent question and I don't have a general answer. If the example are plots generated by commercial software, I would assume that you can publish those. Maybe we can also find examples where this is less clear? If it is research output, you are anyway expected to publish the generated data to reproduce the results.

78. Images online: sorry for the silly question but. What about memes? They are clearly not licensed but it's massively used anyways. Is this a gray area?
    - Yeah, I think it's a big grey area.  Both backgrounds and specific memes would be copyrighted, but it seems that mass use is more valuable than trying to enforce the copyright.
    - They may fall under fair use when used in a readme or on a slide

## Feedback, day 4

Today was:
- too fast: o
- too slow: 
- just right: oooooooooooooo
- useful: oooooooooooooo
- more discussion wanted: 
- more exercise wanted: oo

One good thing about today:
- licensing! +6
- snakemake +3
- I think the active participation by the course participants in the Licensing session was really great and helped make this a very nice session even though there were no exercises +2

One thing that should be improved for next time:
- I found it harder today than last week to listen, keep track of HackMD, fill out polls. Today's content was less familiar, so multitasking was harder +6
- Answers for the polls must be given right next to the question, instead of scrolling back and forth to read question and find corresponding location to answer it +1
   - thanks! I will create an issue for this so we won't forget 
   - issue created
- I was missing proper introductions to the topics, especially in the second part. It was not really intuitive, and I'm not sure how much I'll take from it. +2
    - I'm sorry for the quick parts in the reproducible-research part.  The topic is just so big that it's hard to give enough introduction.  We can try to improve for next time!

Comments on the course format:
- .

Other comments:
- I learned alot today and loved the discussion based formate (which i usually find boring).
- Consider that EL need to check out attendance in their teams, so the breakout rooms are also useful to maintain that connection with the learners. This has an impact on the credits granted.
  - good point. thanks. I did not think about that.  
