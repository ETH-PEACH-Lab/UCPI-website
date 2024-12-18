# Literate Programming

## The struggle with documentation

The documentation of code is essential for people to be able to maintain and reuse code. One common case where good documentation is often sorely missed is when downloading the code from a research paper and trying to understand how it works. The code can significantly diverge from the way it is presented in the paper as there are a lot of technical details glossed over in the paper and the nicest mathematical representation may not be the best computational implementation. In these cases thorough documentation describing how to code lines up with the paper and why for example a value is calculated the way it is, would be greatly appreciated. 
The reality, however, is that documentation is often treated as an after thought. In the rush to get papers published thorough documentation is often neglected in favour of polishing other parts (namely the ones that reviewers are more likely to look at). But, perhaps if we imagine a world where all code is properly documented, the time saved in deciphering other people's code could be enough to also provide proper documentation of one's own code. This is the world envisioned by **literate programming**; A world in which proper documentation is part and parcel of what it means to write a programm.  

## WEB - Where it all began
In 1984 Donald Knuth published WEB the first literate programming language. The guiding philosophy behind literate programming is that one could achieve far superior documentation of code by considering programms as works of literature. Knuth writes: "Instead of imagining that our main task is to instruct a *computer* what to do, let us concentrate rather on explaining to *human beings* what we want a computer to do.". Accordingly, WEB is made to allow authors of programms to narrate their code, interweaving programming language with prose that elucidates what a piece of code should achieve and why it is written the way it is. To achieve this WEB uses two subprocesses called TANGLE and WEAVE that act as intermediate compilers. TANGLE takes the WEB source file and compiles it to PASCAL from where a PASCAL compiler can then compile it to an executable. WEAVE on the other hand compiles WEB to TEX from where it can rendered to a human readable format. In essence TANGLE procudes the WEB programm the computer reads and WEAVE produces the programm that humans read. 
Importantly, the result of WEAVE is not simply a version of the pascal code with extensive comments. An essential part of WEB is the use of named code blocks. Named code block allows authors to write a block of code and refer to it by name to have that code inlined at that location similar to a macro. This lets authors boil down the purpose of a block to a simple description, greatly simplifying the areas of code that make use of the blocks.
For example a function that adds a string to a buffer may have more code dedicated to sanitazing the string then actually adding the string. Thus, an author may begin to worry that the function looks like it achieves a different purpose and cut back on the sanitization. But, by defining a code block "string sanitization" the buffer function will only contain that one line and the "string sanitization" code block can be written as elaborate as it needs to be. 
Another crucial component of WEB is its extensive hyperlink structure which the name WEB is based on. 
#### Required Reading

* [CWEB](http://www.literateprogramming.com/cweb\_download.html): Knuth, Donald Ervin. "Literate programming." The computer journal 27, no. 2 (1984): 97-111.

#### Optional Reading

* [JupyterNotebook](https://jupyter.org/): Lau, S., Drosos, I., Markel, J. M., & Guo, P. J. (2020, August). The design space of computational notebooks: An analysis of 60 systems in academia and industry. In 2020 IEEE Symposium on Visual Languages and Human-Centric Computing (VL/HCC) (pp. 1-11). IEEE.

