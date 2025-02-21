---
description: 'Author: P. Risold'
---

# W7 - Programming Interactive Visualization

## W7 - Programming Interactive Visualization

#### Reading List

**Required Reading**

* [B2:](https://vis.csail.mit.edu/pubs/b2/) Wu, Y., Hellerstein, J. M., & Satyanarayan, A. (2020, October). B2: Bridging code and interactive visualization in computational notebooks. In Proceedings of the 33rd Annual ACM Symposium on User Interface Software and Technology (pp. 152-165).

**Optional Reading**

* [DataParticles](https://rrrima.github.io/dataparticles.html): Cao, Y., E, J. L., Chen, Z., & Xia, H. (2023, April). DataParticles: Block-based and language-oriented authoring of animated unit visualizations. In Proceedings of the 2023 CHI Conference on Human Factors in Computing Systems (pp. 1-15).

## Blog Post

### Programming Interactive Visualizations

Understanding data is a fundamental task and since we humans are visual beings it is no surprise that we like to visualize data in order to better understand it. We may create visualizations to help with the analysis of data itself or to more easily share the insights we gained. First, I will be talking about interactive visualizations in the context of analyzing tabular data, using Tableau (Tableau, n.d.) and B2 (Wu, Hellerstein, & Satyanarayan, 2020) as examples. Second, I will discuss interactive visualizations in the context of sharing insights with data storytelling, using DataParticles (Cao, E, Chen, & Xia, 2023) as an example.

#### Data analysis

Traditionally, you might analyze some tabular data by writing code to filter the data, computing some statistics and visualizing your results in a static plot. You may then repeat this process until you've answered all the questions you had about the data. Interactive visualizations for data analysis offer an alternative workflow. They allow a user to interact with a canvas to select, filter and plot data as desired without writing code. A program with a rich toolbox allows you to do many complex analysis steps with a few clicks. An example of such a tool is Tableau.

**Advantages**

A comprehensive tool for interavtive visualization has many advantages. As mentioned, users don't need to write code, enabling many more people to analyze data. It also tends to accelerate analysis as it can automatically make some choices for you. For example it may automatically generate an appropriate plot based on the data types of the underlying data. Also, the various plots can be managed and structured in canvas in a way that helps keep an overview.

**Disadvantages**

The downside of any interactive visualization tool is that it has a limited set of functionality. Admittedly, this may be a small issue for most users if the toolbox is large enough, but it is a fundamental limiting factor. Another issue is the integration of the visual analysis into a larger pipeline. If, for example, you want to use your data for a machine learning task, moving data between the visualization tool and the computational notebook containing your ML pipeline may be cumbersome.

**Best of both worlds?**

These downsides can be remedied by offering both a code pane and a visual pane that work together. This is implemented by the tool B2. It is a jupyter extension which maintains an interactive canvas in addition to the jupyter notebook. You can select a part of your data through regular manipulation in code in the notebook and then automatically visualize it on the canvas. This allows you to easily get from code to visualization. Alternatively you can also create plots on the canvas directly by interacting with the user interface (UI) of the canvas. The interesting part is that interacting with the canvas through the UI also generates code in a notebook cell. This code allows you to replicate the manipulations achieved by your interactions with the canvas. This allows you to get from the visualization back to code. It is even possible to mark a cell as "reactive". A reactive cell has access to the data currently selected in the plots of the canvas. Whenever a new selection is made inside the canvas, such as selecting a particular bar in a bar plot, the cell is re-executed using just that selection. This allows you to automatically propagate changes in the visualization to code. This bi-directionality of being able to manipulate your data in code, visualize it, further manipulate it in a visual tool and automatically propagate the changes back to code is a great step towards integrating a visual tool into the environment of general purpose coding. It also addresses the issue of a limited toolbox, since you can use code to fill any gaps.

Yet it does introduce an issue of its own. Since working in the visual pane automatically generates code in the notebook, special care is required to not clutter the notebook. Also, the synthesized code is not always easy to understand, making it hard to adjust it and limiting its use to a pure replay mechanism of the canvas interaction. Future progress in code synthesis may improve this.

**Outlook**

With the progress of large language models (LLMs) an obvious step is to incorporate natural language as interface to interactive visualization tools. In fact, Tableau already allows you to request and manipulate visualizations with natural language. Then again, the same can be said for visualizing data through code. LLMs can use visualization libraries to create plots automatically. I would argue that this creates an idependent paradigm which can be combined with any approach, be it a visual tool like Tableau, a bi-directional system like B2 or pure code. In the future I'd expect to see a system which supports bi-directionality between code and visualization. However, the code layer will be accessed by an LLM. If LLMs will be good enough at manipluating the code, then this will not need to be exposed to the user. This would then be the best of both, or rather, all three worlds: Use the regular UI for tasks the UI is suited for and specify arbitrary manipulations in natural language without having to worry about the underlying code.

Of course there is more than just tabular data. There are well over 100 visualization tools for computational notebooks for all kinds of data (Wang, Munechika, Lee, & Chau, 2023). I can imagine that LLMs will allow to unify many tools under one common natural language based interface.

#### Data storytelling

An entirely different kind of interactive visualization is data storytelling, which is about highlighting insights about your data through a textual narrative supported by visual elements. Crucially the visual elements are tied to the underlying data. Such stories are engaging and can make your insights easy to follow. But creating them can take a lot of time, since updating the story means creating new visualizations. This creates the need for tools which automate the visualization creation based on the text of the story. A tool which addresses this issue and creates animated unit visualizations for tabular data is DataParticles. It builds a story from multiple blocks. Each block has a text and a visualization. Words in the text can be marked as key words. You can then define new key words as a selection of your data. Whenever the word is used in the story, the corresponding visualization will treat all elements of that selection as a group. This could for example mean that these elements are highlighted in the same color. Key words can also be associated with data operations, for example calculating the mean, which is then applied to each group of the current block. From this the current visualization is automatically created, including a transition from the previous block.

**Advantages and disadvantages**

Automatic visualization generation accelerates the creation process and prevents inconsistencies between text and data. But it also limits the customization options. Also, Dataparticles works well because it limits itself to tabular data. Extending the tool for less regular data with more komplex relationships would be hard.

#### Author

**Pascal Risold** is a computer science student at ETH experienced at using notebooks for ML tasks and interested in methods to visualize data.

**References**

Cao, Y., E, J. L., Chen, Z., & Xia, H. (2023). _DataParticles: Block-based and language-oriented authoring of animated unit visualizations_. In _Proceedings of the 2023 CHI Conference on Human Factors in Computing Systems_ (pp. 1-15).

Tableau. (n.d.). _Business Intelligence and Analytics Software_. Retrieved from https://www.tableau.com/

Wang, Z. J., Munechika, D., Lee, S., & Chau, D. H. (2023). _SuperNOVA: Design Strategies and Opportunities for Interactive Visualization in Computational Notebooks_. Retrieved from https://arxiv.org/abs/2305.03039

Wu, Y., Hellerstein, J. M., & Satyanarayan, A. (2020). _B2: Bridging code and interactive visualization in computational notebooks_. In _Proceedings of the 33rd Annual ACM Symposium on User Interface Software and Technology_ (pp. 152-165).
