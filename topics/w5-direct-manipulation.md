# W5 - Direct Manipulation

Since the dawn of computing, two paradigms have dominated how we instruct machines: **text-based programming**, where developers write code to define behaviors and computations, and **direct manipulation**, where users interact with software interfaces to adjust and create content visually. Consider the evolution of graphics programming as a case study:

Early video game developers, like Carol Shaw \[[9](#references)\], the creator of 3D Tic-Tac-Toe on the Atari 2600, would write some code, compile and run the program, and watch whether the shapes drawn onto the screen achieved their intended effect. If a point was off or a color felt wrong, they’d then go back into the code and repeat the entire process until they got the design right.  
Nowadays, people use graphics software like Sketch \[[10](#references)\] to draw shapes with their mouse, drag around points, and select from a color picker. The “what you see is what you get” paradigm of direct manipulation is clearly the more natural way of creating vector graphics, and some would argue even to build User Interfaces. Yet, for many tasks, text-based programming remains indispensable. Why?

![A comparison of text-base programming and direct manipulation](./w5-direct-manipulation-media/intro.png)

The power of code lies in its flexibility and abstraction. Developers can encode geometry using mathematical relationships, derive complex shapes from formulas, and build parametric designs that are responsive and reusable. Code allows precise control over the rendering process and can scale complexity in ways visual tools often cannot. That said, thinking in numbers and abstract relationships is challenging, and the iterative, trial-and-error nature of coding adds friction to the creative process.

On the other hand, direct manipulation excels at immediacy and intuition. It provides instant feedback, enabling creators to explore ideas interactively without deciphering numeric representations. But this ease of use comes with limitations. The software's capabilities constrain designers, and output formats like SVG prioritize machine readability over human editability. This often forces a split: designers create static assets in visual tools, and developers adapt them in code for interactivity or animation.

But what if we didn’t have to choose? What if we could directly interact with live program outputs and seamlessly modify the underlying code? This vision lies at the heart of Output-Directed Programming, a novel approach that combines the best of both paradigms.

### A Brief History of Output-Directed Programming

Before its formal definition in 2019 through Hempel et al. \[[1](#references)\], many incremental works shaped its foundations:

![A sampler of related work](./w5-direct-manipulation-media/related-work.png)

Expanding on the core ideas of [Live Programming](./w6-live-programming.md), where people see their code’s output immediately and can travel through time, Sean McDermid’s APX \[[3](#references)\] introduced **mouse-based direct manipulation in code**. Programmers can modify number literals, extract expressions to variables, and abstract code blocks to functions by holding and dragging their mouse cursor in the IDE.

Going beyond in-code manipulations, Schreiber et al.’s Transmorphic \[[2](#references)\] UI framework allows programmers to **directly manipulate a running program**. Using its ‘Halo’ overlay, programmers can rearrange layouts, edit shape paths, and instantiate components graphically.

Mayer et al. \[[4](#references)\] explored a complementary idea: **backporting edits from generated outputs to their source code**. In their prototype, changes made directly to generated HTML or CSS—such as altering a table row’s background color—propagate back to update the corresponding string in an Elm-like codebase.

Finally, unifying ideas from the previous works, Hempel et al. developed **the first output-directed vector graphics IDE** with Sketch-n-Sketch \[[1](#references)\]. It enables three editing features through direct manipulation: Drawing shapes on the canvas, manipulating intermediates displayed via widgets, and refactoring by highlighting subjects and choosing from a menu.

### Looking Beneath the Surface: Successful Methods and Research Questions

Making Output-Directed Programming a reality requires an IDE to understand and synthesize human-like code.

![An overview of existing methods](./w5-direct-manipulation-media/method.png)

Transmorphic and Sketch-n-Sketch use **Abstract Syntax Trees (ASTs)** to map code abstractions—such as functions, arrays, or maps—to interactive widgets, creating a hierarchy like matryoshka dolls. Refactoring options depend on the selected abstraction, enabling targeted edits like inlining or abstraction. This approach works well with **functional languages**, where expressions map directly to visual representations but are harder to get right with imperative languages.

When programmers modify their programs’ outputs, IDEs like APX must precisely understand which values in the source code to update. Building a dependency graph during program evaluation is called **provenance tracing** and suffices for straightforward edits like resizing a rectangle.

However, **complex edits requiring refactoring or new code generation remain an open research problem**. The difficulty lies in ambiguity: infinitely many programs can produce the same output. A naïve approach (ignoring computational infeasibility) might favor the program with the lowest Kolmogorov complexity \[[6](#references)\]—the shortest program that produces the desired output—but this disregards programmer intent and style. For instance, a programmer might start with a triangle when writing a function that generates regular polygons. Hard-coding its vertices is certainly short, but it doesn’t achieve the programmer’s goal of writing a generalizable function taking its center and extent.

To address this, Sketch-n-Sketch lets programmers guide edits by introducing graphical constraints and relationships step-by-step. Its code generation engine employs **heuristics** and **algebraic simplification** (via the REDUCE solver) to propose multiple human-like code samples, allowing the programmer to select the one best aligned with their intent. However, playing around with Sketch-n-Sketch quickly reveals its limitations: as the number of variables grows, the number of ways to express the same constraint increases significantly. This creates a tedious review process for the programmer, who must sift through numerous suggestions or watch as the alignment between their mental model and the generated code progressively deteriorates.

### Towards Accessible and Efficient Interactive Programming Experiences

Needless to say, we are still many papers away from achieving truly bidirectional programming experiences. We **haven’t even reached Turing completeness**. Without writing code manually, programmers using Sketch-n-Sketch can only complete 4 out of the 15 tasks of Potter et al.’s “Watch What I Do” \[[7](#references)\] benchmark.

Recent advancements in code generation, such as GitHub’s Copilot \[[8](#references)\], show promise in bridging the gap between human intent and machine output. However, there remains significant potential to explore novel manipulation UIs and extend output-directed programming to non-visual domains. (How does one represent, say, a network call? How about a database query?)

Encouragingly, elements of output-directed programming are already emerging in the industry. Apple’s Xcode \[[5](#references)\] lets developers modify SwiftUI code by directly manipulating its preview, albeit in a limited way. This provides a glimpse into how such paradigms can make programming more accessible and experimental today while pointing towards the broader vision of efficient interactive programming experiences tomorrow.

> **Alexander Zank <[zank.me](https://zank.me)>**  
> is a Master’s Student in Computer Science at ETH Zürich and a researcher in Human-Centered Computing, focusing on Computational Interaction, User and World Modeling, and Accessibility in Extended Reality (XR).

#### References

\[1\]: [Sketch-n-sketch](https://ravichugh.github.io/sketch-n-sketch/): Hempel, B., Lubin, J., & Chugh, R. (2019, October). Sketch-n-sketch: Output-directed programming for svg. In Proceedings of the 32nd Annual ACM Symposium on User Interface Software and Technology (pp. 281-292).

\[2\]: [Transmorphic](https://publishup.uni-potsdam.de/frontdoor/index/index/docId/9830): Schreiber, R., Krahn, R., Ingalls, D. H., & Hirschfeld, R. (2017). Transmorphic: Mapping direct manipulation to source code transformations (Vol. 100). Universitätsverlag Potsdam.

\[3\]: [APX](https://www.youtube.com/watch?v=YLrdhFEAiqo): McDirmid, S. (2015, September). A live programming experience. Strange Loop Conference.

\[4\]: [Bidirectional Evaluation with Direct Manipulation](https://doi.org/10.1145/3276497): Mayer, M., Kuncak, V., & Chugh, R. (2018). Bidirectional evaluation with direct manipulation. In Proceedings of the ACM on Programming Languages, 2(OOPSLA).

\[5\]: [SwiftUI Previews](https://developer.apple.com/videos/play/wwdc2020/10185): Apple, Inc. (2020, June). Visually edit swiftui views. In Apple Worldwide Developers Conference (session 10185).

\[6\]: [Kolmogorov complexity](<https://doi.org/10.1016/S0304-3975(98)00075-9>) Kolmogorov, A. N. (1998). On tables of random numbers. Theoretical Computer Science, 207(2) (pp. 387–395).

\[7\]: [Watch What I Do Benchmark](https://dl.acm.org/doi/book/10.5555/168080) Cypher, A., Halbert, D. C., Kurlander, D., Lieberman, H., Maulsby, D., Myers, B. A., & Turransky, A. (Eds.) (1993). Watch what I do: programming by demonstration. Cambridge, MA, USA: MIT Press.

\[8\]: [GitHub Copilot](https://copilot.github.com) GitHub, Inc. (2021). Copilot: your AI pair programmer.

\[9\]: [Carol Shaw](https://www.computinghistory.org.uk/det/47370/Carol-Shaw/): The Centre for
Computing History (2004). Carol Shaw.

\[10\] [Sketch](https://www.sketch.com): Sketch B.V. (2024). Designers, welcome home.
