# W6 - Live Programming
## SnipPy: Small-step live programming by example

SnipPy is a tool that combines two user assisting programming paradigms: live programming and programming by example.
Live programming refers to programming environments that provide near-instant feedback, enabling programmers to immediately observe the effects of code changes. This can range from simple tools like REPLs (Read-Eval-Print Loops) to systems like PythonTutor (Week 4) or Sketch-n-sketch (Week 5), which offer visualizations and interactive debugging. On the other hand, Programming by example focuses on generating code by taking input/output pairs as demonstrations. A synthesizer analyzes these pairs and attempts to infer a program that produces the desired results

In SnipPy, live programming is facilitated by projection boxes, which dynamically display the current state of program variables beside each line of code. Programmers can step through the code line by line and observe how the program state changes in real time. This visualization is a powerful aid in writing code, debugging, and understanding new code, as it allows developers to reason visually about how their code manipulates data. (INSERT EXAMPLE IMAGE FOR PROJECTION BOXES)

Building upon this snippy now integrates programming by example into projection boxes. On a new line of code, the user can provide input/output pairs into a projection box and the tool will try to synthesize a matching expression.

The inner workings of the synthesizer are quite easy to understand. It has an abstract grammar that 
represents the possible expressions that can be generated (INSERT EXAMPLES OR EXAMPLE IMAGE).
Note that it is limited to a subset of Python - it can only operate on 
integer and string types and functions whose arguments and return values are of these types.
The synthesizer then recursively generates expressions by expanding the grammar rules, until it finds an expression that matches the types of the input/output pairs. If expression correctly matches the actual pairs, it is returned to the user, otherwise the synthesizer will continue searching for a correct expression until it runs out of time.
To ensure meaningful results, the synthesizer uses a number of heuristics to guide the search, for details see the paper.(NOTE FOR REVIEW: I think going into more technical detail here is not fitting for a blogpost - what do you think?)

Now that we know how SnipPy works, let’s dive into a few examples to see where it shines and where it might run into some challenges: First, lets consider a program that abbreviates names. We give the synthesizer the input/output pairs
- "Adam Smith" -> "A.S."
- "Augusta Ada King" -> "A.A.K."
- "Alan Turing" -> "A.T."

```python
#Synthesized code:
abbreviation = ".".join([var[0] for var in name.split(" ")])
```
This is a concise and correct solution to the problem.
Next, let’s consider an example where we extract the domain name from an email address. Again we provide the synthesizer with input/output pairs: 
- user1@example.com -> example.com
- john@ethz.ch -> ethz.ch
- jane@gmail.com -> gmail.com
- food@mensacorp.org -> mensacorp.org
    
```python
#Synthesized code:¨
    splitchar = "@"
    domain = email[1:-1][email.find(splitchar):-1] + email[-2:len(email)]
```
This solution, while less elegant than the first one, is still correct. However we can see that the synthesizer has some limitations. First of all, the splitchar has to be user-defined, else synthesis fails. Secondly, the solution for some reason first removes the first and last character of the email before extracting the domain, and then adds them back in. This is obviously unnecessary and is an artifact of the synthesizers enumeration based approach - which is not able to reason about the logic of the problem.
Lastly, lets consider a program that takes a list of integers and returns the last element.
- [1, 3, 5, 6] -> 6
- [3, 2, 7, 5] -> 5

```python
#Synthesized code:
    last_elem = len(input_list) + 2 // min(input_list)
```
What? This is absolutely not what we were looking for. (a very simple solution would be ```input_list[-1]```) When doing the math, we can see that the expression is indeed correct for our input/output pairs. However, it is not a correct solution to the problem. This shows that the synthesizer is very bad at using list indeces. Diving deeper into more examples could reveal even more limitations of the synthesizer.

While SnipPy presents an innovative fusion of live programming and programming by example, its current synthesizer
struggles to meet the practical needs of developers.
However, the landscape of code synthesis has changed quite dramatically since the publication of this tool. 
New large language models like GPT, BERT or Claude are able to reason about code and problems in a much more accurate way than the limited enumeration approach of SnipPy. It would be interesting to see how the interface of SnipPy could be combined with an LLM based synthesizer. 
Tools like github copilot function in a similar way - where the user provides a prompt and the tool is able to generate code in-editor.

A promising step in this direction is LEAP, a tool that integrates LLM-based code synthesis with live programming. LEAP generates multiple code completions for a given problem, allowing users to preview the options. Upon selection, LEAP displays the chosen code with corresponding projection boxes based on sample inputs, which visualize the program state. Unlike SnipPy, LEAP primarily uses projection boxes for code verification rather than problem specification. This shift aligns better with the strengths of LLMs, which can reason about prior code context and high-level problem requirements.

In conclusion, SnipPy demonstrates the potential of integrating live programming with programming by example, while its limitations reveal opportunities for more advanced synthesis techniques to enhance developer tools.

### Sources
#### SnipPy
* [Snippy](https://snippy.goto.ucsd.edu/editor): Ferdowsifard, K., Ordookhanians, A., Peleg, H., Lerner, S., & Polikarpova, N. (2020, October). Small-step live programming by example. In Proceedings of the 33rd Annual ACM Symposium on User Interface Software and Technology (pp. 614-626).

#### Live Programming
* [Projection Boxes](https://cseweb.ucsd.edu/\~lerner/papers/projection-boxes-chi2020.pdf): Lerner, S. (2020, April). Projection boxes: On-the-fly reconfigurable visualization for live programming. In Proceedings of the 2020 CHI Conference on Human Factors in Computing Systems (pp. 1-7).
* [PythonTutor](https://pythontutor.com/): Guo, P. J. (2013, March). Online python tutor: embeddable web-based program visualization for cs education. In Proceeding of the 44th ACM technical symposium on Computer science education (pp. 579-584).
* [Sketch-n-sketch](https://ravichugh.github.io/sketch-n-sketch/): Hempel, B., Lubin, J., & Chugh, R. (2019, October). Sketch-n-sketch: Output-directed programming for svg. In Proceedings of the 32nd Annual ACM Symposium on User Interface Software and Technology (pp. 281-292).

#### LLM based code synthesis combined with live programming
* [LEAP](https://doi.org/10.1145/3613904.3642495): Kasra Ferdowsi, Ruanqianqian (Lisa) Huang, Michael B. James, Nadia Polikarpova, and Sorin Lerner. 2024. Validating AI-Generated Code with Live Programming. In Proceedings of the 2024 CHI Conference on Human Factors in Computing Systems (CHI '24). Association for Computing Machinery, New York, NY, USA, Article 143, 1–8. https://doi.org/10.1145/3613904.3642495