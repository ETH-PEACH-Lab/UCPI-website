# W11 - Programming Tutorials and Interactive Textbooks
By Simon Ebner Msc Computer Science

Programming tutorials are essential when learning how to code. The term "Multi-stage tutorial" refers to tutorials that build up to the desired end product in small steps, often annotated with explanations for each step. In this blogpost we will take a look on what makes a programming tutorial great and see what tools exist to help wirte such tutorials. In particular we will discuss "Colaroid" a Visual Studio Code Extension that tries to aid and speed up the process of writing such a multi-stage tutorial.

### The Essence of Multi-Stage Tutorials
Multi-stage tutorials can vary greatly, depending on who writes them and the environment in which they are presented to a reader.
Let's take a look at some factors that can influence the learnign experience.
#### - Capturing the Authentic Coding Experience 
For a tutorial to be easy to follow and to apply what has been learned effectively, it should illustrate the thought processes and the decisions that a developer would have made during the process of coding.
#### - Providing Context to Code Changes
When displaying the changes in code per step it is important that the reader has enough context to understand why and where something has been changed. Ideally a reader would have access to the whole codebase at each step to be able to compare different timesteps in a tutorial.
#### - Displaying all intermediate Results
By letting a reader see the results of the code at every timestep (if there are any), they can gain an understanding of what each change does. This visual feedback helps learners see the immediate impact of their code, reinforcing learning through direct observation. It's beneficial to include screenshots, outputs, or even live demos to illustrate these intermediate results clearly.
#### - Interactive Environments
"Learning by doing" is a core aspect of our modern understanding of teaching. One way of incoorperating this into a programming tutorial is to make the environment interactive.
This allows the readers to play around with the code and try out different values and ideas and directly see the effects.


### Authoring Tools
Creating tutorials that include some of the above mentioned features is a difficult and time consuming task. To ease the burden on the authors there exist a few Tools already. Some previous tools recorded the full developement process and allowed to comment certain checkpoints and create tutorials that way [1] or automatically decompose an existing code example into multiple independent stages [2].


#### - Jupyter Notebooks
Jupyter Notebooks are commonly used for computer science courses and academic research. They provide an online interface based on the literal programming approach [3], that works in any browser. 
It allows to combine runnable code snippets and text. Benefits of this environment are that you can describe each code snippet as extensive as you see fit, it can easily be shared and it provides an interactive experience for the readers.
But there are a some drawbacks aswell, such as allowing for out of order execution of the cells and doesn't encourage best practices [4]
#### - Torii
With Torii, authors can build tutorials on top of already existing code by creating snippets of that code. These snippets can be augmented with descriptions and code outputs. They can be flexibly reordered and repeatet without affecting the outputs.
It also automatically propagates changes in a snippet along all code snippets and outputs. [5]
### Colaroid
Colaroid is a Visual Studio Code extension designed to assist in creating multi-stage tutorials for web-developement. During the process of writing code, the author can create snapshots that capture the entire codebase at that specific point in time. As with most other tools mentioned before, the snapshots can be extended with descriptions and the outputs of the current code.
As opposed to previous tools, colaroid notebooks provide readers with the complete code base where the changes compared to the previous snapshot get highlighted.
With this readers have a clear overview where the change has been made. This is especially useful when dealing with multiple files as is often the case in webdevelopement.

The outputs are fully interactive and support a feature where authors can record an interaction within an output which will then be shown to readers.
Authors can make changes to earlier snapshots. Colaroid will then try to propagate these changes by merging the 2 branches if possible. If there is a merge conflict it will keep the newer snapshot but not propagate any changes. This can in a few cases lead to incosistent code snapshots, which Authors will have to manually fix.

Colaroid has shown to achieve great satisfaction with both authors and readers. Authors positively remarked on the ability to edit snapshots and being able to record interactions within outputs. While readers said they felt more engaged than with classic tutorials or with video tutorials.

Currently Colaroid is limited to webdevelopement, as the output features work best when producing visual outputs. But the basic system could easily be expanded to other programming domains.
It is also limited to Visual Studio Code and doesn't work in any other coding environments.

### Outlook on the future of programming tutorial tools

Programming tutorials will most likely stay relevant in the future, and therefore will be more and more tools developed to simplify the task of writing these tutorials. Obviously we have to talk about how machine learning could be of use here. Large language models in particular might be of interest as for example one could imagine a feature where a model automatically writes a first draft for descriptions of code snippets or a chatbot that further explains certain parts of a tutorial.
Aside from machine learning, tutorials could further be expanded with more interactability like exercises or even gamification depending on the intended userbase.


### References
[1] Mark Mahoney. (2018). Storyteller: a tool for creating worked examples. J. Comput. Sci. Coll. 34, 1 (October 2018), 137–144.

[2] Sanchez, H., Whitehead, J., & Schaf, M. (2016). Multistaging to understand: Distilling the essence of java code examples. https://doi.org/10.1109/icpc.2016.7503708

[3] Knuth, D. E. (1984). Literate Programming. The Computer Journal, 27(2), 97–111. https://doi.org/10.1093/comjnl/27.2.97

[4] Johnson, J. W. (2020). Benefits and Pitfalls of Jupyter Notebooks in the Classroom. Proceedings of the 21st Annual Conference on Information Technology Education. https://doi.org/10.1145/3368308.3415397

[5] Head, A., Jason Zheng Jiang, Smith, J., Hearst, M. A., & Hartmann, B. (2020). Composing Flexibly-Organized Step-by-Step Tutorials from Linked Source Code, Snippets, and Outputs. https://doi.org/10.1145/3313831.3376798