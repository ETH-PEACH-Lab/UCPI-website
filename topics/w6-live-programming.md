# W6 – Live Programming  
## SnipPy: Small-Step Live Programming by Example  

Live programming is a development paradigm that offers immediate feedback by showing how code behaves as it is written.
This real-time interaction allows developers to observe variable states, program output, 
and the effects of changes instantly, which can improve understanding, debugging, and iteration. 
The concept encompasses a range of tools, from simple REPLs (Read-Eval-Print Loops) to more advanced systems 
like PythonTutor ([Week 4](https://pythontutor.com/)) and 
Sketch-n-Sketch ([Week 5](https://ravichugh.github.io/sketch-n-sketch/)), 
which provide visualizations and interactive debugging.  

Despite its benefits, live programming faces challenges such as cognitive overload from constant updates, 
scalability to larger programs, and limited support for abstract or complex problem-solving. 
These challenges have inspired tools that combine live programming with other paradigms to enhance usability 
and functionality.  

One such tool is **SnipPy**, which integrates live programming with programming by example (PBE). 
By doing so, it not only offers real-time feedback through **projection boxes** but also uses **input/output pairs** 
to synthesize code on the fly. This blog explores how SnipPy works, where it excels, and where it struggles, 
while situating it in the broader context of live programming.  

## How Live Programming Works  

The core idea of live programming is **immediacy**: as developers write code, the environment updates to reflect changes in the program state. 
This approach eliminates the traditional compile-run-debug loop, providing continuous feedback.  

Modern tools like **projection boxes** take this a step further by dynamically displaying variable 
states next to the corresponding lines of code. 
This helps developers visually track how data flows through their program in real time. 
For example, in a tool like PythonTutor, users can step through code execution line by line and see 
visualizations of how variables evolve.  

These capabilities make live programming particularly useful for:  
- Debugging: Quickly identifying where and why code behaves unexpectedly.  
- Learning: Helping new programmers understand how individual lines of code affect program behavior.  
- Incremental Development: Allowing developers to experiment with changes and immediately observe the results.  

However, as program complexity increases, the constant feedback can become overwhelming, 
and existing tools often struggle to scale their visualizations or interactivity effectively.  

## SnipPy: A Fusion of Live Programming and Programming by Example  

SnipPy builds upon live programming by integrating it with programming by example (PBE). This combination enables users to both observe program execution through projection boxes and generate new code expressions by providing input/output (I/O) pairs.  

### How It Works  

- **Projection Boxes:** SnipPy uses projection boxes to display variable states beside each line of code in real time. This allows developers to see how program data evolves as they step through the code. For example, if a loop iterates through a list, the projection box shows how the list’s elements are accessed and modified. (INSERT EXAMPLE IMAGE FOR PROJECTION BOXES)  
- **Code Synthesis via I/O Pairs:** On a new line of code, users can provide I/O pairs in a projection box, and SnipPy’s synthesizer attempts to generate a Python expression that matches the given behavior.  

#### The Synthesizer  

The synthesizer operates on a restricted subset of Python, limited to integer and string types 
and functions with compatible arguments and return values. Using an **abstract grammar**, 
it recursively generates candidate expressions until it finds one that matches the I/O pairs. 
If no match is found within a time limit, the synthesis fails. To improve efficiency, 
the synthesizer uses heuristics to guide its search.

### Examples  

Let’s explore a few examples to see SnipPy in action and examine its strengths and limitations.  

#### Example 1: Abbreviating Names  

Input/Output Pairs:  
- `"Adam Smith"` → `"A.S."`  
- `"Augusta Ada King"` → `"A.A.K."`  
- `"Alan Turing"` → `"A.T."`  

**Synthesized Code:**  
```python
abbreviation = ".".join([var[0] for var in name.split(" ")])
```  
This is a concise and correct solution that demonstrates SnipPy’s ability to handle string manipulations effectively.  

#### Example 2: Extracting Domain Names from Email Addresses  

Input/Output Pairs:  
- `"user1@example.com"` → `"example.com"`  
- `"john@ethz.ch"` → `"ethz.ch"`  
- `"jane@gmail.com"` → `"gmail.com"`  
- `"food@mensacorp.org"` → `"mensacorp.org"`  

**Synthesized Code:**  
```python
splitchar = "@"
domain = email[1:-1][email.find(splitchar):-1] + email[-2:len(email)]
```  
While this solution works, it is unnecessarily convoluted. For example, 
it removes and re-adds parts of the string redundantly, 
reflecting the limitations of SnipPy’s enumeration-based synthesis.  

#### Example 3: Returning the Last Element of a List  

Input/Output Pairs:  
- `[1, 3, 5, 6]` → `6`  
- `[3, 2, 7, 5]` → `5`  

**Synthesized Code:**  
```python
last_elem = len(input_list) + 2 // min(input_list)
```  
This output, while mathematically correct for the given pairs, 
clearly fails to generalize to the problem’s intent. The synthesizer struggles to reason about list indices, 
a limitation of its grammar-based approach.  

## Limitations of SnipPy and Opportunities for Improvement  

While SnipPy demonstrates the potential of integrating live programming with PBE, 
its limitations highlight broader challenges in live programming:  

1. **Cognitive Overload:** Projection boxes can clutter the interface in more complex programs, making it hard to focus.  
2. **Quality of Synthesized Code:** The synthesizer often generates correct but inelegant solutions, or even brittle ones that fail for broader input ranges.  
3. **Limited Scope:** The tool’s restricted grammar and data types reduce its utility for real-world applications.  


## Future Directions  

The advent of large language models (LLMs) like GPT or Claude offers a promising path forward. 
These models can reason about broader code contexts and generate more accurate and elegant solutions 
than enumeration-based synthesizers.  

One tool exploring this potential is **LEAP**, which combines LLM-based synthesis with live programming. 
LEAP generates multiple code completions for user evaluation and visualizes the corresponding program state 
using projection boxes. Unlike SnipPy, LEAP focuses more on validating and refining code rather than purely generating 
it. This aligns better with LLMs’ strengths in reasoning about high-level problem context.  

## Conclusion  

SnipPy illustrates the exciting possibilities of combining live programming with programming by example, 
but its limitations underscore the need for more advanced synthesis techniques. Looking ahead, 
integrating LLMs into live programming tools could enhance their usability and effectiveness, 
allowing developers to harness real-time feedback without being hindered by the system’s constraints.  

As tools like LEAP demonstrate, the future of live programming lies in striking a balance between automation, 
interactivity, and developer control. By addressing current challenges, 
these tools can unlock new possibilities for faster, smarter, and more intuitive coding experiences.  



### Sources

#### SnipPy
- [Snippy](https://snippy.goto.ucsd.edu/editor): Ferdowsifard, K., Ordookhanians, A., Peleg, H., Lerner, S., & Polikarpova, N. (2020, October). *Small-step live programming by example*. In *Proceedings of the 33rd Annual ACM Symposium on User Interface Software and Technology* (pp. 614-626).

#### Live Programming
- [Projection Boxes](https://cseweb.ucsd.edu/~lerner/papers/projection-boxes-chi2020.pdf): Lerner, S. (2020, April). *Projection boxes: On-the-fly reconfigurable visualization for live programming*. In *Proceedings of the 2020 CHI Conference on Human Factors in Computing Systems* (pp. 1-7).
- [PythonTutor](https://pythontutor.com/): Guo, P. J. (2013, March). *Online python tutor: embeddable web-based program visualization for cs education*. In *Proceedings of the 44th ACM technical symposium on Computer science education* (pp. 579-584).
- [Sketch-n-Sketch](https://ravichugh.github.io/sketch-n-sketch/): Hempel, B., Lubin, J., & Chugh, R. (2019, October). *Sketch-n-sketch: Output-directed programming for svg*. In *Proceedings of the 32nd Annual ACM Symposium on User Interface Software and Technology* (pp. 281-292).

#### LLM-based Code Synthesis Combined with Live Programming
- [LEAP](https://doi.org/10.1145/3613904.3642495): Ferdowsi, K., Huang, R., James, M. B., Polikarpova, N., & Lerner, S. (2024). *Validating AI-Generated Code with Live Programming.* In *Proceedings of the 2024 CHI Conference on Human Factors in Computing Systems (CHI ’24)*. Association for Computing Machinery, New York, NY, USA, Article 143, 1–8. <https://doi.org/10.1145/3613904.3642495>