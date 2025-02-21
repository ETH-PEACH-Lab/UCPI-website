# Leveraging Visual Debugging for Programming Education

Teaching programming can be a challenging task. Whether you're introducing coding to beginners or helping more advanced learners grasp complex concepts like scope, recursive function calls, or aliasing (when multiple names refer to the same object), understanding how a program works is often a significant hurdle. One of the most effective ways to overcome these challenges is visual debugging, a method that makes it easier to understand programs.

In this blog post, we’ll discuss the role of visual debugging in programming education, focusing on *Python Tutor* [1], a tool that uses program visualization to teach programming concepts.

### What is Visual Debugging?

Debugging is a common process in which developers inspect and fix errors in a program. Traditional debugging methods rely on logs and stack traces, but visual debugging uses intuitive visuals and interactive tools to make it easier for software developers to gain a deep understanding of programs, and for instructors to teach programming concepts.

Traditional debuggers allow you to step through code in a text-based interface. On the other hand, *Python Tutor* displays the relationship between objects and visualizes data structures, helping students form a clearer mental model of the program.

Another way to debug programs is to use print statements. Its simplicity and versatility make it the most popular debugging method among programmers [2]. However, if you have many print statements in your code, interpreting the output can be difficult because it's often just a heterogeneous stream of text. This makes it hard to see where the printed value is coming from. The Visual Debugging Tool *Log-it* [3] offers structural and interactive visuals to help developers gain a deeper understanding of the logs.

### The Challenges of Teaching Program Execution

A key challenge in programming education is helping students understand how a static piece of code (the source code) translates into a dynamic process (program execution).  
Instructors often use graphical PowerPoint slides or draw diagrams on a whiteboard to explain this process, but both methods require a lot of preparation and can be prone to errors.

### What is Python Tutor?

*Python Tutor* is a free, online tool that lets users write, execute, and step through Python code directly in their browser. It provides a visual, interactive debugger to help learners understand how their code works in real-time, showing how variables change, illustrating control flow, and tracing function calls.

What sets *Python Tutor* apart from other visualization tools is that:

-   It uses Python which is a beginner-friendly language because of its simple syntax and prepares students well for advanced computer science courses [4].
-   Unlike other tools, Python Tutor requires no complex installation or setup - it only needs a browser, without any plugins.
-   It’s super easy to embed in websites - all you need is to include an HTML element in your webpage.

### How Python Tutor Works

1.    The user writes Python code in the browser and submits it to the backend server.
2.    The backend takes Python code as input and uses Python's debugger (bdb) to execute it step by step and record the program’s state after each line of execution.
3.    After the program has finished, the execution history is converted into JSON with metadata and sent back to the browser.
4.    The browser leverages this data to provide an interactive, step-by-step visualization of the program's execution. The user can navigate through the execution by stepping forward or backward to observe how each line of code impacts the program’s state, which includes an easy-to-understand visualization of the control flow, call stack, and objects in the heap.

### Extending Python Tutor

*Python Tutor* was originally centered around Python 2, which was the predominant version at the time, it has since transitioned to defaulting to Python 3, now the more commonly used version [5].

It has also expanded to support additional programming languages, including Java, JavaScript, C, and C++.

The platform has also embraced AI integration, offering a "Get AI Help" feature that generates prompts for submission to a language model. Currently, the feature only creates the prompt without sending it.

### Final Thoughts

Visual debugging is one of the most effective tools for making programming accessible to students of all levels. It transforms abstract processes into interactive, comprehensible experiences, helping learners grasp complex concepts with ease. By visualizing code execution step by step, tools like *Python Tutor* enhance understanding and engagement. These tools are particularly beneficial for visual learners and those who find it challenging to understand abstract concepts, such as recursion, through traditional text-based methods.

As AI-assisted tools become increasingly prevalent in the programming world, visual debugging tools like *Python Tutor* stand to gain immensely from AI-driven advancements. These enhancements could include providing smart suggestions, identifying errors, and even generating code snippets tailored to the learner’s needs. The next logical step is to fully integrate AI capabilities into visual debugging tools, paving the way for more seamless and interactive experiences. This integration remains an exciting frontier, offering vast opportunities for innovation and improved learning outcomes.


### References

[1] Guo, P. J. (2013, March). Online python tutor: embeddable web-based program visualization for cs education. In Proceeding of the 44th ACM technical symposium on Computer science education (pp. 579-584).  
[2] Clark, B. (2017, April). Debugging in Node.js. https://www.clarkio.com/2017/04/25/debugging-in-nodejs/#debugging-progression  
[3] Jiang, P., Sun, F., & Xia, H. (2023, April). Log-it: Supporting Programming with Interactive, Contextual, Structured, and Visual Logs. In Proceedings of the 2023 CHI Conference on Human Factors in Computing Systems (pp. 1-16).  
[4] R. J. Enbody, W. F. Punch, and M. McCullen. Python CS1 as preparation for C++ CS2. In Proceedings of the 40th ACM technical symposium on Computer Science Education, SIGCSE ’09, pages. 116–120, New York, NY, USA, 2009. ACM  
[5] JetBrains (2024). Python Developers Survey 2023 Results. https://lp.jetbrains.com/python-developers-survey-2023/#python-versions
