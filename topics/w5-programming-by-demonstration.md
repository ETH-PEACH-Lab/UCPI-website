# W5 - Programming by Demonstration

### Reading List

#### Required Reading

* [Helena](https://helena-lang.org/): Chasins, S., & Bodik, R. (2017). Skip blocks: reusing execution history to accelerate web scripts. Proceedings of the ACM on Programming Languages, 1(OOPSLA), 1-28.

#### Optional Reading

* [Flashfill](https://support.microsoft.com/en-us/office/using-flash-fill-in-excel-3f9bcf1e-db93-4890-94a0-1578341f73f7): Gulwani, S. (2011). Automating string processing in spreadsheets using input-output examples. ACM Sigplan Notices, 46(1), 317-330.

#### Blog Post

##### Introduction

Making an inanimate thing perform actions automatically after demonstrating what you want it to do has been a dream for a very long time. No logic that has to be thoroughly thought out and no knowledge of a programming language, simply demonstrate what you want to get done, and the artificial creation itself figures out what you want from it. As with so many things in life, reality is usually disappointing.


For a program to understand what you want, you usually need to program each action, define what it needs to do for each edge case and even then it might not work as you want it to. For a program to learn from demonstration adds another layer of complexity on top of it, where it has to for example visually, through a video input, or mechanically, through a movement performed by moving the robot arm, understand what you want and then do the programming itself, which then guides the movement later. With the added computation power and layer of programming that needs to be done, it is no wonder that the term "programming by demonstration" has only appeared about 30 to 40 years after the first artificial intelligence research, or at least the research that became the basis for AI. Programming By Demonstration is still about 40 years old, quite a bit of progress has already been made and still has a lot more potential for improvement.


##### Not quite PBD

The simplest form of letting the computer perform tasks shown by the user is an auto-clicker[[1]](#1). A program often used by gamers or people trying to automate a specific task, without doing coding. It records mouse movement, the timing of the clicks, and for more advanced versions which windows the clicks were performed on. When replaying the clicks, it can add random delays to throw off bot detection software and some auto-clickers can start operations at defined times. Although this software "learns" what to do, all it is is a replay with some noise, there is no rule generalization, there is no adaptation to the user inputs and there is no decision-making, that the tool needs to do. That is also why it is not a PBD tool.


##### Rule-Based PBDs
An example of a rule-based programming by demonstration tool is a chess robot[[2]](#2). The PBD part is done by moving the robot through the desired motions and teaching it when to perform these actions. The robot can accumulate actions and perform each at the desired point in time. This seems like the auto clicker, but it has to understand the 3D movement and generalize it, for each scenario decide what to do and the movements could be reused for different tasks.


##### Programming Synthesis-Based PBDs

An example of Programming Synthesis-Based PBDs that a lot of people might be familiar with is the Flash Fill[[3]](#3) Excel feature.
By performing several actions on subsequent cells, the program observes the editing done and proposes similar edits for subsequent cells, be it based on other cells, a math formula, or date and time patterns, just to list some examples. This program fits much more our description of learning, it generalizes what it has seen and can perform similar actions further. It is programming synthesis-based because it infers a program, based on the demonstration of the user.


Another example of a Programming Synthesis-Based programming by demonstration program is the Rousillon tool[[4]](#4), a Helena-based browser extension, which also relies on the Ringer library. This Rousillon browser extension is a web scraping tool, which uses Ringer to observe the scraping actions for the generation of the first row of data and generates a low-level script that can repeat the performed action. Then it runs the code through a Generalizer, which creates a high-level script, that generalizes the performed scraping, creating similar actions to collect more data in the same fashion. The important parts of the script are then demonstrated to the user in a block-like way, in the style of Scratch. This script can then be edited, and then run on the Helena Interpreter to collect the web data. 


This program, although good on paper, when tested by us, often didn't perform. The whole extension relies on a centralized server, which is used for the Generalizer to better generalize actions, but in turn makes it very slow and completely non-private. Very often it doesn't work at all, again because of the server. And even if it works, it is a very inefficient way to gather data, since it relies on the program clicking in the graphical user interface, rather than making direct server requests.
It generalizes on the performed actions and learns the patterns, as well as writes a code, which is generated by using the found patterns. 


##### LLM-Based PBDs

An example of LLM-based PBDs would be a tool that uses an LLM to extend the capabilities of Flash Fill. The user could demonstrate the creation of a cell, based on a text or a more complex logic, which Flash Fill would struggle with, and the LLM could then create the next cells automatically. Due to the LLMs and ML algorithms recently having a huge spike in use and performance, most PBDs still use mostly heuristics so this field is the most unexplored and probably the one with the most potential. This is especially true, since PBDs based on AI could better adapt to situations and users, which will lead to better performance[[5]](#5).


##### Some big hurdles in PBD

We have seen examples of UI automation with auto-clicker, which could become a PBD tool with added features that generalize actions, automated data collection with Rousillon, robotics automation, and data completion with Flash Fill. There is still a lot of room for improvement in these areas, as well as, automated data analysis, IoT configuration, and ML training. However, for each of these, there are common roadblocks that need to be overcome to make a usable PBD tool, which each need to be addressed in every PBD.


For one, the PBD needs to accurately understand what was demonstrated. This can be challenging since demonstrations can often be missing important parts, or be ambiguous, and difficult to interpret for the PBD. This hurdle can usually be avoided by either creating clear guidelines for the demonstrator, limiting the inputs that can be shown, or using heuristics and having a large database of previously shown demonstrations and their correct outcomes, like Rousillon. Another possibility is using large language models to interpret what was shown or fill in the gaps in the demonstration.


On the other hand, a big hindrance is also, how to show to the user, what the PBD tool understood from the demonstration. Is it a dumbed-down version in an easily readable high-level language enough in Rousillon? Or how many examples does it need to demonstrate to show that it understood the pattern in Flash Fill?


Additionally, if several demonstrations have been performed, how to contextualize these if they are for one behavior or multiple. Will it be able to find a good enough pattern to do the correct thing for most situations? What if we want it to almost never make mistakes, like in a medical environment, where a mistake could be the difference between life and death?


##### Outlook for the future of PBD tools

The limits of programming by demonstration haven't been pushed, they aren't even in sight yet. With the recent development boom in the area of artificial intelligence, PBD can definitely benefit from it. Having a house robot do the chores doesn't seem as far, now that many companies have developed robots that already are doing regular tasks, like barista robots and warehouse robots. To make one of these robots perform a new chore, you could, for example, demonstrate the desired chore, and the robot will then be able to replicate that chore. Another avenue can be the creation of an application, where a designer can show prototyped user interfaces and how they should transition, and the PBD program could program the app to look and perform as desired. The future for programming by demonstration is very promising since the result could be programming of actions, without the need for a programmer.\\

At least this is the dream of many who are not versed in programming, since programming development can take quite a long time and relies on communication with the client, on what the client wants in the product. The premise of reaching a point, where no programmer is needed, is that the program has to understand what the client wants, better than a group of trained programmers who are also human. Additionally, the assumption is that the client knows what they want and how it should be implemented. Even with the development of AI, we have not reached a point, where AI can program better than professionals. What we have reached is that AI can help professionals write code faster. Combine the AI with task-specific heuristics and an interface optimized for programmers, and you get that PBD will help developers, like many other tools, develop faster, and there lies the true opportunity for programming by demonstration tools.


#### References
<a id="1">[1]</a> 
Auto-clicker: opauto-clicker.com (2023). 
Example of a simple auto-clicker.
https://www.opauto-clicker.com/

<a id="2">[2]</a> 
Chess robot: A. Billard, S. Calinon, R. Dillmann, & S. Schaal (January 3, 2008). 
Chess robot that uses Programming by demonstration to learn chess. 
https://calinon.ch/papers/Billard-handbookOfRobotics.pdf

<a id="3">[3]</a> 
Flashfill: Gulwani, S. (2011). 
Automating string processing in spreadsheets using input-output examples. 
ACM Sigplan Notices, 46(1), 317-330.

<a id="4">[4]</a> 
Rousillon: Chasins, S. E., Mueller, M., & Bodik, R. (2018, October). 
Rousillon: Scraping distributed hierarchical web data. 
In Proceedings of the 31st Annual ACM Symposium on User Interface Software and Technology (pp. 963-975).

<a id="5">[5]</a> 
PBD with AI: Paynter, G. W., & Witten, I. H. (2004, Chapter 8). 
Applying machine learning to programming by demonstration. 
Journal of Experimental & Theoretical Artificial Intelligence, 16(3), 161-188.
