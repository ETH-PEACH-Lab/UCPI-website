---
description: 'Author: A. Boyle'
---

# W6 - Literate Programming

### The struggle with documentation

The documentation of code is essential for people to be able to maintain and reuse code. The reality, however, is that documentation is often neglected \[6]. In particular in research, the rush to get papers published often leaves no time to clean up and document the code. This leads to a vicious cycle where the time spent deciphering other people's code uses up the time to write documentation for one's own code. But, perhaps if we imagine a world where all code is properly documented, we could instead have a positive feedback loop where the time saved by high quality documentation is again invested into documentation. This is the world envisioned by **literate programming**; A world in which proper documentation is part and parcel of what it means to write a program.

### WEB - Where it all began

In 1984 Donald Knuth published WEB the first literate programming language \[1]. The guiding philosophy behind literate programming is that one could achieve far superior documentation of code by considering programs as works of literature. Knuth writes: "Instead of imagining that our main task is to instruct a _computer_ what to do, let us concentrate rather on explaining to _human beings_ what we want a computer to do.". Accordingly, WEB is made to allow authors of programs to narrate their code, interweaving programming language with prose that elucidates what a piece of code should achieve and why it is written the way it is. To achieve this WEB uses two subprocesses called TANGLE and WEAVE that act as intermediate compilers. TANGLE is used to produce the machine-readable version by compiling WEB to pascal and WEAVE is used to produce the human-readable version by compiling WEB to TEX.

Importantly, the result of WEAVE is not simply a version of the pascal code with nicely formatted comments. An essential part of WEB is its hyperlink structure. The output of WEAVE produces an index of all defined functions showing where they are defined and referenced, the prose can reference other relevant parts of the code and outside sources et cetera. This structure makes a WEB program eminently more searchable than the equivalent pascal program.

Another crucial part of WEB is the use of named code blocks. Named code blocks allow authors to write a block of code and refer to it by name in other parts of the code. In the output of TANGLE, the code block is then in-lined at that location similar to a macro. This lets authors boil down the purpose of a block to a simple description, greatly simplifying the areas of code that make use of the block.

For example, a function that adds a string to a buffer may have more code dedicated to sanitizing the string then actually adding the string. Thus, an author may begin to worry that the function looks like it achieves a different purpose and cutback on the sanitization. But, by defining a code block "string sanitization", the buffer function will only contain that one line and the "string sanitization" code block can be written as elaborate as it needs to be, improving the code.

### Computational Notebooks - The present state of literate programming?

In his original paper Knuth writes: "I made a conscious decision not to design a language that would be suitable for everybody. My goal was to provide a tool for system programmers, not for high school students or for hobbyists". He writes that the profusion of languages involved in WEB introduces a large variety of potential bugs and syntax errors, the complexity of which is more suitable for computer scientists than hobbyists to handle. Ironically, however, literate programming never really caught on in systems programming \[3] and instead is presently more used in beginner friendly, high-level programming interfaces \[2] and in particular is popular for tutorials \[4]. Among these interfaces, computational notebooks are often cited as the contemporary form of literate programming \[2], because notebooks similarly allow users to interweave exposition blocks with code blocks. This, however, is a rather superficial comparison in certain key aspects.

The main aspect wherein literate programming and notebooks diverge is that literate programs in the vein of WEB produce executable binaries of the same form as the equivalent illiterate program. In particular, this means that authors do not need to worry about their programs being less performant simply for having written them in a literate fashion. In notebooks, however, the execution paradigm is often completely different from the equivalent illiterate program, which can lead to much worse performance and significantly more crashes.

Moreover, unlike Knuth's form of literate programming where the literate language should be an extension on top of the original language that is kept as simple as possible, notebooks provide a lot of extra functionality. For example, notebooks may provide block level execution, integrate the output into the file itself or provide better options for code sharing. When asking users why they use notebooks it appears that these other features, more so than the literate aspect of text blocks, are what contributes to the popularity of notebooks. In this vein, one may argue that using a computational notebook is not literate programming, but rather a form of programming that happens to integrate some of the ideas of literate programming.

### AI - The future of documentation

Modern IDEs also incorporate a lot of the features that WEB brought to the table like pretty printing, and an extensive hyperlink structure. With the introduction of large language models (LLMs) into the programming workflow the process of IDEs taking on all the features of literate programming may come full circle. GitHub CoPilot already allows users to easily generate docstrings for their functions, often only requiring small corrections here and there. Similarly, as code is increasingly written by LLMs, the prompt used to generate the code could be added inside the code as a sort of literate documentation, an idea already introduced by \[5]. AI also presents a myriad of other opportunities to add documentation for the code and one could easily imagine a tool for converting illiterate programs to literate ones via AI.

However, when AI takes over the "literate" part of literate programming, a key motivating factor behind Knuth's work is lost. Namely, that writing programs in a literate fashion not only makes programmers write better documentation, but also makes programmers write better code. Knuth writes: "My original idea was that WEB would be merely a tool for documentation, but I actually found that my WEB programs were better than the programs I had been writing in other languages." and that this is "because the new methodology encourages me to do a better job."

### Conclusion

If we view documentation as being part of a program, then one can see how literate programming makes the authoring of a program easier. However, many programmers may disagree with that presuposition and actually see literate programming as increasing their workload. Accordingly, they may choose to ignore the literate aspects of a literate programming tool or have AI take over for them. Thus, while a tool may ease programmers into writing literate programs, it cannot guarantee that the resulting artifice is actually of the literate form that Knuth envisioned.

It may be argued then, that no tool will ever be a literate programming tool nor will any interface be a literate programming interface. Instead, there will be programmers who write literate programs and those who do not.

#### About the author

My name is Alan Boyle and I am a CS master student majoring in machine intelligence. Because of my interest in natural language processing I, like so many others, have been drawn to large language models (LLMs). In my most recent work I developed an interface for LLM explainability as part of my research on improving explainability methods.

### References

\[1] Knuth, Donald Ervin. "Literate programming." The computer journal 27, no. 2 (1984): 97-111.

\[2] Lau, S., Drosos, I., Markel, J. M., & Guo, P. J. (2020, August). The design space of computational notebooks: An analysis of 60 systems in academia and industry. In 2020 IEEE Symposium on Visual Languages and Human-Centric Computing (VL/HCC) (pp. 1-11). IEEE.

\[3] Pieterse, V., Kourie, D., & Boake, A. (2004). A case for contemporary literate programming. In Proceedings of the 2004 Annual Research Conference of the South African Institute of Computer Scientists and Information Technologists on IT Research in Developing Countries (pp. 2–9). South African Institute for Computer Scientists and Information Technologists.

\[4] April Yi Wang, Andrew Head, Ashley Ge Zhang, Steve Oney, and Christopher Brooks. 2023. Colaroid: A Literate Programming Approach for Authoring Explorable Multi-Stage Tutorials. In Proceedings of the 2023 CHI Conference on Human Factors in Computing Systems (CHI '23). Association for Computing Machinery, New York, NY, USA, Article 798, 1–22. https://doi.org/10.1145/3544548.3581525 April Yi Wang, Andrew Head, Ashley Ge Zhang, Steve Oney, and Christopher Brooks. 2023. Colaroid: A Literate Programming Approach for Authoring Explorable Multi-Stage Tutorials. In Proceedings of the 2023 CHI Conference on Human Factors in Computing Systems (CHI '23). Association for Computing Machinery, New York, NY, USA, Article 798, 1–22. https://doi.org/10.1145/3544548.3581525

\[5] Horvath, A., Macvean, A., & Myers, B. (2024). Meta-Manager: A Tool for Collecting and Exploring Meta Information about Code. In Proceedings of the 2024 CHI Conference on Human Factors in Computing Systems. Association for Computing Machinery.

\[6] E. Aghajani et al., "Software Documentation Issues Unveiled," 2019 IEEE/ACM 41st International Conference on Software Engineering (ICSE), Montreal, QC, Canada, 2019, pp. 1199-1210, doi: 10.1109/ICSE.2019.00122. keywords: {Documentation;Software;Tools;Maintenance engineering;Taxonomy;Interviews;Information services;Documentation, Empirical Study},
