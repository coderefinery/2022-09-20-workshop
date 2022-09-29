+++
template = "page-with-toc.html"
title = "Questions and notes from workshop day 6"
+++

## Icebreakers

### What tools do you use for testing code?
  - Assert, try-except, raise Error oooo
  - unittest oo
  - pytest
  - cargo test
  - catch2
  - visualize my workflow on data  o
  - logging o
  - printing outputs and see if the result make sense oooooooooo
  - junit

### Tell us some about this course:
How did you attend (alone home/work, small group home/work/online, organized group, ...):
- Organized group in person ooooooooooo
- Alone at home ooooooooo
- Zoom group from university: ooo
- Alone at work: oooooo

What would be the ideal format for this course?  (e.g. like this, in-person, videos available and scheduled Q&A/mentoring sessions, etc.)
- Like this is amazing, streamed freely and if you want you do exercises, and with access to the material. ooooooooo
- I like it this way (zoom group from own university, watching the stream and post questions on HackMD) o
- Studies on-campus are already difficult for someone at a distance of more than one hour from campus. When it is not required by the content of the course, it is very welcome to be online.
- Like this. I think that the teaching can be streamed or video material, and it is nice to have a small live group where to watch it together, communicate and do the exercises - and get help. 
- Teaching/theory on video, exercises and such livestream/on-site
- In-person sessions aren't that fun unless there's actually exercises to be done. So if you want more people in person, less type-along and lecture type material. But I quite enjoyed this format. +1
- I really like a format like this, online. In person courses, for me, have more value when there is a more social aspect during exercises, but this is by definition coding and doing exercises on your own computer, so I find an online format works very well. I am doing this alone, I see some people do it in small groups, which is also a nice way to do it.

Other feedback
- Consider adding Scala as another "supported" language for the courses, since Aalto teaches based on it programming to the undergraduate programs.
    - thanks 
    - would you like to help us add it?
        - I wish I had the confidence, but I'm still learning under huge time pressure (i.e. about x4 time per weekly assignments compared to the "estimated required"). But I will try to contact you regarding that once I'm better prepared skill-wise.
- I would have assumed that this course requires some coding skills, which actually have not been needed. I think many people would not attend because they might feel that they lack the good enough coding skills. 
   - thanks +1

## Questions

1. Where can I find the collaborative documents of the previous workshop days?
   - https://coderefinery.github.io/2022-09-20-workshop/questions/

2. I can hear you!
   - Matteo is slightly louder than Richard, but not by much
   - better?
     - sounds good.

## [Software testing](https://coderefinery.github.io/testing/#software-testing)

### [Motivation](https://coderefinery.github.io/testing/motivation/)

### [Concepts](https://coderefinery.github.io/testing/concepts/)

3. To the shown example: I'll check also that it returns a number, that that number is within a given range, etc
   - Agreed to the extent, that you need to ensure, that a different type of return value cannot pass the test.
   
4. Do I need to test the test function, then test the test of the test fuction, and so on...?
    - I'd argue: no. If your test function doesn't work, it's the same as a policy not being followed. 
    - A micro-controllers teacher told me once "Building test is more an art that an exact science". There's no correct way to test functions and projects once they grow enough. With a small Celsius to Fahrenheit function the test is self-evident, but when your function/code does more complex stuff when sometimes the output is not always proportional to the input (or even random) tests become more and more complex.
        - You can still try to get as close to testing that it does what is intended as possible. e.g. if you have an optimisation function with random starting points that aims for local optima, you can at least try to see if it returns better results than just the random inputs, or, you can test for a few known local optima of some known functions and check, whether those are found. But I agree, that writing good tests can be very challenging
    - You might want have the functionality your tests rely on to be tested (like that assert throws errors, if the assertion is wrong), but one would hope that this is done in the code that introduces these functions.
    
5. One of my last famous mistakes was to type a sine instead of a cosine. It was a oneliner. The quantity of ink does not matter. It is the value of the operation that matters for me.
   - the most difficult bugs for me were often one-liners
   - somebody taught me: when you find a bug, look into recent commits since bugs seem to surface soon (but there is also git bisect)
    
6. Any (binary) test can produce false/true positives/negative. So I think you should test the test. This is the issue of sensitivity and specificity and the topic of the confusion matrix. See https://en.wikipedia.org/wiki/Confusion_matrix
    - We have seen this with the medical tests for covid-19. 
        - Exactly there is a control on the test to ensure its working correctly. Similar to placebo when testing effectiveness of medication
    - I would argue that this is something somewhat different to code-testing.
        - Disagree still. It's about asserting the reliability of a test, that is any assertion after a control. Obviously a virus is different from an operation. But the purpose of a test on either is the same: produce an assertion, which can be true or wrong based on the reliability of the test itself.
        - See also https://coderefinery.github.io/testing/concepts/#tests-don-t-guarantee-correctness
          - I guess it depends on what you consider testing the test. Yes, I agree that not checking the test for actual correctness makes sense, but writing test functions for tests is not the way to do that (in my opininon)
    - My typical solution here would be multiple independent tests.  If one test fails but others do not, I am forced to look deeper and will notice the problem is in the other test.
        - +1
          
7. Is testing for one value enough? Like in the case of the Fahrenheit to Celcius.
   - I'd argue no, because it doesn't protect against someone replacing the function by `return valueX`.... 
       - How much is enough? How do we test in a more general way?
         - I'd say as long as the amount of work necessary to hard-code the individual results is higher than just writing the actual functionality. But that could lead to a lot of tests.
   - What follows is more defensive programming than a fully fledged test. Anyhow... In case of a division it may be wise to test for a condition that the denominator is never zero (and provide an alternative code route if the exception occurs). In that case you test all the values that end up in the denominator.
      
8. Does mixing defensive programming and unit testing make stuff unorganised or complicated?
   - No. Actually you can test your defensive programming assertions, and you should. 
   
9. Many languages have some sort of `assert` function vs a `raise` or `throw`. Can you expand on the **conceptual** difference (regardless of the technical ones)? What is the philosophy behind those type of functions?
    - "Assert" is designed to be something that should never happen if the code/input is running normally.  So, Python provides a way to ignore assertions if you need to run slightly faster.
    - Exceptions should be used for things that might happen even if the code is running as expected.

10. Is Triton down?
    - Yes, short maintenance.  Are you using it for exercises?
        - Yes. I have my env only there

### [Testing locally](https://coderefinery.github.io/testing/pytest/)

11. If the floating point number has the problem, like 0.1+0.2= 0.30000000000000004. Why do people still use the floating point number, instead of decimal datatype? In other words, what is the additional cost to use decimal datatype? Would the error of the floating point be amplified in a large numerical simulations and cause numerical convergence issues? 
    - Because it is much, much faster for computers to use.  And the downsides aren't too bad in most cases.  When needed, you can use a decimal datatype in languages. (e.g. python `decimal`)
    - There are whole studies dedicated to understanding floating point errors and handling them.  Which is needed, because decimal types would be too slow for those large simulations that need them...

### Exercise Local-1,2
Everything on this page: https://coderefinery.github.io/testing/pytest/
Second on optional, OK if you can't do anything (next exercise starts over)

I am:
done: ooooooooooooooooo
wished for more time:
not trying:
exercise was good: 
exercise needs improvement: 

10. Hi, could you please add me to an exercise group? Should I email support? OK, then can I ask questions later? If so, how? Can I send an email to support?
    - me too ! also i cant hear audio from twitch stream, not sure whats reason (unmuted, refreshed already, no audio before break even). may be i can join on zoom?
    - Right now there is a break and no audio.  Yesterday, refreshing Twitch fixed audio for someone.  Also you may need to unmute Twitch.
    - There is no zoom way to attend, though CR had another learner zoom that needed pre-registering.
    - CR support email is support@coderefinery.org

11. I don't really understand the purpose of this exercise. From my understanding pytest helps you to find syntax errors in your code. But isn't that something that Jupyter notebook or R studio doing anyway? And writing code in nano seems a bit unnatural to me.
    - It's not syntax errors, but logic errors.  And you need logic to find those errors.
    - Testing is also for future development. I.e. you want that any modifications to your (basic) function do not change results that were done before the change. So in any larger project you want to ensure that changing an underlying function does not make other functions invalid.

12. So just like I use try-except to handle exceptions, I should also be using assert in my python code to catch errors that should never happen? 
    - You don't have to, but assertions make sure that some inputs are invalidated (e.g. in the kelvin conversion if you assert the input > 0, you make sure that no invalid inputs are used), which would give results that are simply wrong because impossible.

13. What is the reason behind `!pytest -v example.py`? I found it just test twice.
    - Hm, it first makes me think "that is a jupyter shell command".  Where is it exactly?
    - In the exercise, there is a hint for us to try inside Spyder or IPython.
    - Ah, yeah.  So, that lets you run the shell command without leaving the Python environment.  `!` means "this isn't python but shell"
        - Why should it run twice?

14. On the Local-2 exercise, the 0,1+0,2 is meant to fail but mine is passing the test. (Python 3.10.6, MAC OS Monterey 12.4) Why?
    - What OS/Python version are you running?
    - interesting hardware architecure? Normally 0.1 +0.2 is not precisely 0.3 (due to floating arithmetic), but seems like either your machine, or some other part does a correction. 
    - Can someone test on different Python versions?  Fails on 3.9
    - Fails on 3.8 (ubuntu 20.04)
    - Fails on 3.10.4 (ubuntu 22) o
    - Fails on 3.10.6 (ubuntu 20.04)
    
15. Question about the optional exercise: I can use any arbitrary number or I can use approx. What is the mechanism of approx. Does it also use any small number?
    - Depends on your application, how exact you want to be. For many aplication 3 significant figures could be enough.
        - I am just trying to understand if/how approx is better than the arbitrary number method
        - I think that both will work. And you can specify the tolerance in the parameters I guess.
        - Yeah both will work, but approx has the advantage of not having to specify a precise boundary (e.g. 1e-7). As a good practice, any number "out of the blue" will make the code less readable
     - The description of pytest.approx might give some hints why approx is better. Basically, it's a bit smarter: https://docs.pytest.org/en/7.1.x/reference/reference.html#pytest-approx

16. When working with code that takes constantly changing data as input (say, a live database), how should we think about testing data import functions etc? Assert reasonable values? Have a small, artificial dataset to use exclusively for testing? other?
    - I usually would try to make small, artifical data for testing.  But it can be a combination of strategies.
    - This could also be a great place to test the robustness vs unexpected errors, like what does your function/tool do if the sensor provides gibberish due to an error, will it just go on, or does it error out?
    - follow-up: if the code then gets shared, would the artificial data be included on the git repo to ensure everyone can run tests? I assume yes?
        - yes. What I personally do iseither have the test data directly integrated in the same folder as the tests, or have a test data directory that somewhat mirrors the structure of the code. 
        - And be careful with real data. That should not be personal data (or only your own personal data).

17. How do I incorporate tests when my input and output are more complex? Like `pandas.Dataframe` or `numpy.array`?
    - E.g. by testing parts of your dataframe. using small examples. like np.array([2,3,4]) as input. Yes, tests can become quite long but they are often worth the effort since a good test can often be reused as an usage example for documentations with minimal adaption.
    - You can also test at different levels. You can test whether the outputs are of the correct type/dimension, as well as checking a few points and see if they are correct. 

### [Automated testing](https://coderefinery.github.io/testing/continuous-integration/)

18. Why "sorry for the Italian"? :-) Should we be sorry for you? ;-) (I'm Italian too)
    - Yeah but I'm Swiss ;) But we got a beautiful language, you're right! I take back my apology.
    
19. I have code that does I/O with a database, do you have advice on how to test that this code correctly inserts, reads and deletes data in the database?
    - What I would do is something along the lines of:
      ```
      data = XYZ
      addressofsubmitteddata = writeData(data)
      dataFromDB = readData(addressofsubmitteddata)
      assert data == dataFromDB
      insert(newPoint,positionInData,addressofsubmitteddata)
      dataFromDB = readData(addressofsubmitteddata)
      assert dataFromDB[positionInData] == newPoint
      ```
      and similar for delete. Is this understandable? *To some extent, but i am not familiar with a means of getting an address for database data (or maybe I'm not getting the abstraction), also the insert and newPoint I do not get*
    - check pytest "fixtures"

20. When I tried to push the file I got the following error:
    ```
    fatal: 'origin' does not appear to be a git repository
    fatal: Could not read from remote repository.

    Please make sure you have the correct access rights
    and the repository exists. 
    ```
    - I found the problem, I didn't access the repository after cloning.

21. So no tests are done on the branch pushed?
    - No, because it was not set up.
    - Ok so not automatically set up on the branch? 
        - I might be wrong, but I think actions need to be set up for each branch. In the action definition you have:
          ```
            on:
              push:
                branches: [ main ]
              pull_request:
                branches: [ main ]
          ```
          where you define when your action is run.
          - we could see that a test is done when doing the pull request. That makes sense. Like a safeguard against breaking main branch. 

22. It seems running the tests on Github is quite slow - we haven't even introduced a very large testsuite yet
    - Starting up the tests is not very fast, but it's not supposed to be your "testing ground", you should normally make sure, that the tests succeed on your machine before pushing. The Github side mainly tries to ensure the quality of your online repository. 
    
23. With automated testing we do not get any notification of the test outcome if we push from the terminal, do we?
    - I think this depends on your notification settings. The action is performed, and if you are notified of action results, then you will get an email.
    
24. If I am working on my own project, it would more sense to me to test just locally? But if I am in a collaborative project, git testing ensures everyone's code is tested?
    - If you do test on Github you show others that your tests succeeded. Otherwise they don't see it.

### [Test design](https://coderefinery.github.io/testing/test-design/)

### Exercise until xx:40
Your choice of exercises here (decide what is most interesting to you): https://coderefinery.github.io/testing/test-design/

Write your thoughts and answers below.

Poll (multi-choice):
- I am done: oo
- I'm not trying: 
- needed more time:o
- good exercise: ooo
- needs improvement: 

26. In design 8, is the idea to use repetitive-test.txt as the well-defined test-input or should we have another file for test definition and then use repetitive-test.txt as the "real world scenario"? And would a reasonable solution include a file such as non-repetitive-test.txt as the correct result?
    - My interpertation is that `repititive-test.txt` is the sample input.  And yeah, including pairs of (input, expected_output) would make sense for this.  Run through each pair, run on the input, compare to the output. Some inputs are hand-made to have a known output, some could be long and random and only for regression tests.

27. I am wondering if design test would also include assuming the user to have the correct behaviors. For example, in Exercise Design 1, it assumes that `n` is a number, while the user could potentially pass a string to `n`, like `drop all` or `rm *`.
    - Good question!  In this case, I am confident the function will raise an exception when it doesn't have a number, which might be good enough for me.
    - Also, It would be reasonable to make a test that verifies the function raises an exception when it's not a number.
    - And assertion if you want a nicer error message than the TypeError you would get.

28. Following Question 27, but in a more general perspective, how could the developer code in a way to prevent users with bad intentions? For example, the user intentionally gives inputs like `rm *` or drop all tables. 
    - This gets to the topic of security, and a big deal.  If you have user input and there are security concerns, you want to be very careful in validating input.
    - Assertions about the input, ensuring that interpreted elements are not arbitrary (log4j bug...) and similar things. 
    - ... though I wouldn't use `assert` here if it was Python, to me that is stuff that doesn't happen.  `python -O` will remove assertions.
        - Would you use assertions to define ensure input type of a function? Or how would you handle it?
        
29. In design 4, I don't understand the input to the test function, the *monkeypatch*. It is an object from another module? I understand the concept of monkeypatching but not the implementation.
    - This is a `pytest` convention, and is *not obvious* by any means.  This is a "fixture" which provides some feature.  In this case, it says "set max_temperature on `reactor` to `100` and undo it when the function is done".
    
30. With these test functions don't you have the risk that you might not find a good (anti)example and then the test itself fails? In other words, that there is a bug but, with the examples you choose you don't find it.
    - Yes, that is always an issue. In principle you try to write your tests as general as possible. If you find a new bug, you extend your tests to cover that bug (or write a new test that checks for exactly that bug). Yes, tests are not a foolproof way to avoid bugs, but they commonly help in maintaining code quality and they particularily help in keeping functionality stable (i.e. they make it less likely, that a change breaks code depending on the tested functionality)

31. Ideas for testing randomness?
    - Do statistical tests
    - Check what is know about the distribution, i.e. dice roll is integer and >=1 and <=6
    - Drive the distribution to one extreme that can be known.
    - Since we don't ever have true randomness, use some way to "fix" the randomness and calculate your results with those "random" numbers. 

32. If a function operates with numerical inputs/outputs, then I suppose that the best way to test it is just to plot its outputs for a wide range of inputs.
    - That depends a bit. I was working with linear programming optimizers, where multiple optima could exist, and the exact one was not necessarily achieved. But you could e.g. test, that the optimal value returned is the within the tolerances set for the solver for a given known optimum. That doesn't mean it needs to find a specific solution, but the optimal value that solution generates is correct (within the respective tolerances).

## [Modular code development](https://coderefinery.github.io/modular-type-along/)

A. What does "modular code development" mean for you?
- What does modular code development mean? +3
- I'm not really sure but I suppose something like...that my code consists of "modules", which can be moved and used in some other code. (I'm thinking about modular synthesis in electronic music and the way that you can change the output of your signal by changing the order of the signal processing modules.)
- Lots of small general classes +1
- Divide workload and liability in a large group
- The ability to reuse a lot of the created methods without the need to make extra adjustments 
- Be clear on different steps in data processing
- A function that performs one task, not thousands of tasks.
- Many functions working separately which can be reused in different projects +1
- That I can copy-paste a function/module/package/portion from one project/notebook into another and it still works
- Modulation helps when one person works only on a part of the code
- I can recognize/recall where I did what, and then why
- Have one short main code and many modules imported

B. What best practices can you recommend to arrive at well structured, modular code in your favourite programming language?
- Think before you act, at times
- Keeping functions simple and pure to combine well with other code
- Type hints in python (so you're confident in reusing code)
- Make functions (and code in general) as general as possible, not only working for the current case, as the code may be reusable in the future and modifying it later may be harder than right now.
- Have a good system architec design to begin with
- Create functions when possible
- Give clear comments for each part of the functions

C. What do you know now about programming that you wish somebody told you earlier?
- Document your code! +1
- Always use functions instead of scripts (for my use case) - it can make your life so much easier down the line.
- Learn the proper way to set up a code, instead of jumping in and code random lines that seem to work.
- Do not use C++ when you can code in Python, life is too short for C++.
  - In some fields it's impossible to ignore, and there is tooling to make it nicer to work with.
- Ignore a lot of the "that's not efficient" talk - you spend weeks on coding and seconds on computing, so don't worry too much about efficiency when you are starting.
    - I think the important bit here is "when starting". Later on, you could either improve performance yourself, or ask others, who might be better at coding to help with improving the performance (like RSEs).
        - Agreed, but I think many people suffer very early on from a clear case of "the perfect is the enemy of the good", and have efficient lines of code in a buggy or incomplete program, or start using C++ to shave seconds of a simulation that could've been developed in half the time in Python.
- In general, I've had a problem in my life that teachers and mentors just give "algorithmic instructions" that I need to follow to learn what's necessary. Everything should be explained so clearly, through metaphors and demonstrations, that I (or anyone else) *actually understands* what is happening.
- Programming languages are about syntax, you don't need read a lot of theory before starting to code. Just start and search for help on the internet when needed.
- A simple and non-fancy code that works reliably (and is readable) >> fancy non-readable code that may or may not work.
- There's this tool called 'git' and how easy it is to use, and how much it helps with version control +1
- Collaborating with people is the most important, which also means that you should use the most common programming language in your field (as long as it is Python ;) ), and spend a lot on time on cleaning, documenting and straight up communication.
- Paper and pen, yet
- Do not try to rewrite the legacy codebase if it already works well.
- Team up with somebody and mentor each other
- Never assume that your script/function will be only used by you, no matter how simple the script/function is.
- Even if working alone, there are always three collaborators involved: you, your past self, and your future self. Be kind to your collaborators.

### What should they do next / comments?

 - Make a function! ooooooooo
    - With one input which is the number of data for x
         - then you can call it with the different values
    - We can also pass the name of the csv file or the kind of data we want to plot, if they will be asked later on.
    - Could the args be filename, columnname and numbers of points?
    - Another plotname
        - plot name could also be generated from number of input points + predefined prefix o
        - Better!
    - make multiple functions!
        - plotting
        - mean()
        - reading()
        - ?
     - Need to change the figure filename!
     - Put the title and stuff into the loop
       - Use string interpolation to put the number into the title  
- Make a repo for what you're working with so you can start tracking your changes!
    - make a README.md-file
- num_measurements isn't necessary as you can can use len(data).

- Make a for loop to plot 3 times

- Document the code and explain why you're doing this 

- Depending on your supervisor, you might get away with 3 repeats of code but I would do the function pretty much as soon as I realise the asks won't stop there.

- Request. Would you share the `history` of your shell? Later, I meant, as a text file kind of `history > history.log`. 
  - Relayed via chat, hopefully we will remember to add it here.

- 33. Question about modular code development in general (maybe you're getting to it soon): when we have small functions that combine to a larger whole, is it better to have the larger whole shared as a script or use wrapper functions and hide more of the behind-the-scenes stuff? Ie script that is 100+ lines or layers and layers of wrapper functions? By wrapper functions I mean larger functions that call the small, modular functions (e.g. preprocess_data() that depends on 20+ other functions vs a script that is called preprocess.py where the smaller functions are more evident to the user).
    - I'm not quite sure what you mean by wrapper function here.  Functions in other files?
    - In my cases, I would often try to divide up into small functions, but (at the start) they are all in one standalone file.  Later on, if needed, I can split the functions out into a library that can be imported - if it ever gets that far.
    - Ah.  Well, I think you naturally get that kind of hierarchy when it makes sense.  Sometimes it does, maybe sometime not.  (I'm sorry for the non-answer but hopefully you figure out the best solution for each case).
        - thanks! So at least there isn't any "commonly agreed best practice" about always showing as much as possible or hiding as much as possible (of what steps happen behind the scenes etc)?

- 34. If you create a general function and you test it for your case, how do you know you can copy it to another project? You haven't tested it for this new use case. Would you then test this new use case?
    - I should have created another notebook and tested it. thanks.

- 35. Can you create a test which resets these input values to empty before running (like matlab clear all or something?)
    - This is a good point and is part of test design.

- 36. Would a better name be plot_data_with_meanline()?
    - Following on this - and it would be possible to derive mean inside the function. as well, not to have it as argument?
    - Sort of depends on the scope of the function -- there's a bit of conflict between generic functions and a reasonable number of parameters
      - this is very apparent with the plotting libraries themselves where functions often have *a lot* of parameters
    - Yes!  I agree.  The best solution I know (which may not work everywhere) is the generic function returns the figure/axes object, which can be modified at the higher level (= don't try to add arguments for everything).  Or the function receives the axes object to plot onto.  Both of these require some care and knowledge to do well.
      - This seems like a good strategy to me.

- 37. What about the formatting of your plot? I think this is often difficult where you put this because you typically always tweak this a bit for the specific case 
     - See above for my take. *Ok, thanks for the tip*.

- 38. Maybe it should be read_temperates() -- no need to overabstract?

- 39. If you sometimes need to plot two (or more) traces in the same plot, is there a good suggestion to encompass this? or should you then just make a separate function that handles plotting multiple traces?

-  40. In general, whenever I write code with many small pure functions, that combined solves a complex task I am always unsure of how to combine them - like which functions should call the other functions to assemble the workflow, can you comment on this problem?
    - super question. we will pick it up.
    - might also need a longer written answer which I will provide in the afternoon

 - Can you switch to the HackMD when you are talking about a question in it?
   - Hopefully they notice this, if I (broadcaster) do it it will get confusing.
   - Thanks

- But what if you use a different data type? How do you know that compute_mean() works with all data types? For example (len(data)) sometimes has unexpected behaviour depending on the data type.
    - currently you do not know, we could tell python what datatype to expect by defining it in the function call
    **- ??? By typing? Or another way?**
    - we'll bring it up after the command line interface
    - Great! Thnx

- 41. Sometimes we add/remove input variables of a function. Is it a good idea to always have just a single input variable, which is just a list, and then refer to its components inside the function?
    - You can add new arguments with default values, and then it is backwards compatible.
    - Or use keyword arguments, and then order/adding/removing doesn't matter so much.
    - If you want to remove a non-keyword argument, you have a problem with backwards compatibility.
    - Consider backwards compatibility when adding new arguments: do you change the default behavior?

- 42. Would it be good to back up with Github, or something similar? I really wanted to see this done in real time.
    - done

- 43. Another common issue for me is in a datapipeline, at a specific step, you would often have a set of functions to choose from depending on what analysis you wish to do. Is there a nice way to handle this? Some way to sort of inject a number of datamanipulation functions in to a step in a datapipeline.
    - Yes, this is a good question of design and takes some knowledge
    - There are differest strategies, but you could have an argument that selects the function by name (or you just pass the function itself in).  Or configuration files, each run gets told which configuration it should use, it finds that run name from the configuration file and uses that selection.
    - *Thanks, maybe someone knows of repos that implement solutions to this that I can check out?* 
    - I wish I knew of some good examples, but I'm not sure where to point.  We hope that an upcoming livestream course https://scicomp.aalto.fi/training/scip/workflows-2023/ will cover this in more detail, but we still have to design the course!  Want to help? *Maybe - am I eligible for attending? :p I do not get from your get-in-touch-link who I would talk to to help *
        - Well, it's a livestream course so... contact via this email if not at aalto: https://scicomp.aalto.fi/help/#email.  Or use the CodeRefinery chat (link in the workshop outro, coderefinery.zulipchat.com).
    - This doesn't have examples of this right now, but I aim to add some examples here as I develop them: https://github.com/AaltoSciComp/hpc-examples/

- 44. Again, what is the `ve` command in the command history? After he edited the requirements file and before he staged it.
    - He has an alias that automatically creates a Python virtualenvironment (makes environment, adds packages from requirements.txt)
    - I will share in the afternoon
        - Thx

I use fish instead of bash and this is fish's way of defining an alias/shortcut. In short, the "ve" creates a virtual environment if it does not exist yet, activates it, and installs into it dependencies it reads from `requirements.txt`. The important point here is that I like installing dependencies from a file because it will force me to document my dependencies. I recommend to do the same for `environment.yml` (how this is done is less important and sorry for introducing yet another thing here, fish, but it's the shell I use):
```
function ve
    if not test -d venv
        python -m venv venv
    end
    source venv/bin/activate.fish
    if test -e requirements.txt
        python -m pip install --upgrade pip
        python -m pip install -r requirements.txt
    end
end

function ce
    eval $HOME/miniconda3/bin/conda "shell.fish" "hook" $argv | source
    if not test -d env
        conda env create --prefix ./env --file environment.yml
    end
    conda activate ./env
end
```

- 45. Add a main function!
     - thanks

- 46. Basic question; what is the difference between installing requirements and this command (can't see it now, import?) on top of the script?
    - Requirements defines packages needed
    - pip+virtualenv (or other tools) installs the packages
    - `import` (if that's what it is) loads packages that are already installed, but doesn't find or install them if not already there.

- 47. Set type=int for num-measurements
    - Thanks

- 48. Pandas series
    - Thanks

- 49. Datasafety when cloud computing results based on unpublished data in a jupyternotebook? - use jupyternotebook instead of jupyterlab maybe? Like when sharing with colleagues. 
    - another way is to share a notebook with non-sensitive publich example data and that can all be public. and then separately distribute the unpublished data.

- 50. I have a question from Day3 collaborative distributed version control. a) Step F. I am confused with what is being pushed to where. We clone the directory the instructor created, then we make a branch and create a text file in the branch. in Step F we push, but there I get lost. b) About forking workflow. I have a super basic question. Why do we need a fork? Why not just work with local clone and central? In Step E, why do we push to fork first and then pull request from fork? Why don't we want to directly pull request from clone to central? Thanks.
    - a) In step F we push the local branch to the exercise repository. Once this is done, please open the exercise repository in your web browser and check whether you can find your branch there. The next step then is to open a "pull request" (change proposal) from your branch towards master
    - b) This is to emulate the situation where you want to make a change to a repository but where you are not a "collaborator", in other words you have read permissions (since it's public) but no write permissions. For such repositories where you are not part of the group, you need to fork first before you can make any modifications. Of course you could also clone directly the central repo and make modifications on your laptop. That always works.
    - why create PR from fork to central and not send PR from clone to central: pull request (PR) is a merge request between one branch on GitHub towards another branch on GitHub (or from GitLab to GitLab; within the same repo or from one repo to another but still on the same platform). when using GitHub you need to have the change on GitHub before creating a pull request from it. It is not enough to have the change on your computer. And since you in this case cannot write to central, you need to write the change to fork first before opening the PR.
    - Thank you. Understood. 

## Afterparty here now:
**You can meet the instructors on Zoom right after we finish**
and anyone want to meet for dinner in helsinki area?: 

## Feedback

Today was:
- too fast oooooo
- too slow o
- just right oooooooooooo
- useful oooooooooooooo
- recommendable oooooooooo
- needs improvement before recommendable oo

One good thing about today:
- Radovan, he's such a great teachter. ooooooooooo 
- I kind of had an idea about testing as something big and scary and hairy before today. I feel like you managed to make it much more approachable and comprehensible. Thank you for that! oo
- Radovans session was great, would be good to have more sessions like this. 
- I would like a dedicated session on how to use Jupyter and Github as a solitary tool for backup (not just the collaborator perspective, first make sure to secure our own production)
- Learning a bit about automatic testing
- very useful day, thank you! 
- Lot's of useful stuff today, need to include more training. The first session of the day was way too fast. Good with write along excersises, but can sometimes be too fast. 
- Good stuff!
- The lesson about modular code was super, helped me to understand a lot +1
- Thank you very much for CI excercise, especially GitLab section (I did it in GitLab) - I will definitely direct my colleagues to this ecxercise, and looking forward to setup automatic linting and testing for our projects!. 
- The course was excellent! Keep the good work!

One thing to be improved for next time:
- The first testing exercise was really easy, but we got a lot of time for it.oooooooo
- would love to have had time to properly go through the more thorough testing examples (but of course the time is scarce)o
- The type-along this morning (automatic testing) was too fast ooooo
- The last workover type along was difficult to follow in the end 
- One nice thing would be if you knew of projects that use the same tools and concepts as described in the course that you could recommend for inspiration (you present some in the course material, but if there are projects that use most or all of the tools that you demonstrate in one project it would be great) 
- maybe say some more about CI/CD this concept is quite widespread but is still somewhat vague to me 
 
Other comments:
- I am completely new to the coding but learned lot. +1
- Really like the documentation you guys have on CodeRefinery o
- I *think* this may have been my first time attending a full day of coderefinery workshop (I think I have previously just dropped in on individual sessions) and I loved the warm & approachable vibe you managed to create despite the distance teaching mode. That is really difficult and you did great! +1
- **THANKS** so much to everyone involved, I learned so much and am excited to apply this in my work life. oooooooo
- Open Access of the course material and video are really valuable part of the course. +1
- You mentioned there was a cheat sheet, at least for the Git-stuff, but I didn't catch where to find it? 
    - In general a niceness to the course would be to have a short-n-sweet cheatsheet for the material covered in the course (maybe this could be generated simply from some of the summarizing text-boxes)
- I think you do a great job of teaching this course! The material is really good and comprehensive also. I was surprised about how well the *otherwise quite passive* online stream actually worked in combination with the HackMD interaction. Kudos for your efforts! 

What would you like to do next:
- Experiment & learn further. What a useful course!
- Have lunch! +1
- More sessions where we do the full walk from initializing repo, starting with a code base, doing the Jupyter notebook, modularizing, testing, making som developmental branches, making issue, merge request, publishing code in a binder. We almost got there today but would be nice to do it a couple of times over. Doesnt need to be complicated code. The important thing would be to do the whole "lifecycle" a coupple of times. +1
- Starting my own repository and applying all that I have learned. +1
- Many (some) questions about how these tie together into workflows, looking forward to the feb workflows workshop! until then I'll try to strengthen up the basics based on these materials
- Save the material of this course for studying it again later
    - Addition to comment above. Please tell me i can access these lectures for ever! I have a lot to catch up on and absolutely loved this workshop. 
        - They should stay online as long as the CodeRefinery project is funded, and the sources are on Github, so as long as Github doesn't close down they can be hosted elsewhere.

- A question: where can I find some instructions for uninstalling the coderefinery environment and creating my own?
    - uninstalling an environemnt: `conda env remove -n coderefinery`, installing your own: https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html
- can we find the stream from last and this week recorded somewhere?
    - for the next two weeks on twitch, after that I think they will be on youtube ( https://www.youtube.com/channel/UC47aupE7HKGduAjXKt1Gwrg )
- Where is the readme file that Richard is showing right now? linked from schedule - https://github.com/coderefinery/workshop-outro/blob/master/README.md

- A course on parallelizing code?
    - There are some resources around on the web. Main issue is that it commonly highly depends on the actual code you have, the language (and libraries) you use and whether the code is parallelizable at all, or if the overhead from trying to parallelize it is not worth it. It also introduces the problems of concurrency... 
        - gotcha, thanks
