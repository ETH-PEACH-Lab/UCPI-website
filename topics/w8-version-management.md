---
description: 'Author: R. Chan'
---

# W8 - Version Management

### _Code Gathering - Version management for dealing with the messes of rapid prototyping in Jupyter Notebooks._

Using **version management** is standard practice in software development. Tools like `git` have many functionalities – branching, merging, reverting, ... - that allow for effective collaboration through version control. In fact, many of us have previously written more or less exactly the following lines:

```
git add .
git commit -m "update"
git push
```

Version management has many benefits, such as easy collaboration, and tracing back or recovering older code versions, as shown in a typical development workflow illustrated below.

![Version management with git enables collaboration, traceability, and recoverability.](https://raw.githubusercontent.com/ETH-PEACH-Lab/UCPI-website/refs/heads/main/topics/img/version-management.png)

The benefits of version management are not only relevant to large-scale productionalized codebases, but also coding environments that work on smaller scales, such as the rapid and exploratory prototyping and data analysis frequently implemented in _jupyter notebooks_. However, managing Jupyter Notebook versions using standard versioning tools such as github is [notoriously difficult and messy](https://github.com/brian-rose/notebook_diff_tutorial). This raises the following questions:

* What messes or conflicts may arise during such prototyping? Which ones may be addressed by (automated) version management?
* How can we adapt "traditional" version management to notebook development such that it addresses developers' needs?

This blog post mainly discusses the 2019 CHI paper _Code Gathering: Managing messes in computational notebooks._ \[1], and its broader impact around version management for computational notebooks.

## Messes in Notebooks

Developing code in jupyter notebooks is... a messy process. Getting to a final version may take many iterations of exploration, testing, and cleaning up during development. (An interesting related study in the reading list analyzes this process in more detail; [Code code evolution](https://doi.org/10.1145/3544548.3580997)).

![Version management with git enables collaboration, traceability, and recoverability.](https://raw.githubusercontent.com/ETH-PEACH-Lab/UCPI-website/refs/heads/main/topics/img/notebook-development-smaller.gif)

During exploration, it is natural to prioritize discovery over writing high-quality code. However, when it comes to sharing or going back on old results, most analysts would want to first clean up their code to

1. keep track of old versions of notebook code, and
2. be able to have portable (minimal) snippets of code, which they can easily copy and re-use.

**But why are these things even hard?** To answer this, the authors first evaluate the issues that commonly arise when developing code for notebooks, which make the aforementioned goals generally difficult. Namely, they are:

* **disorder**: because of the [persistent jupyter kernel memory](https://hex.tech/blog/jupyter-kernel-overview/), code may be developed out of execution order. If the kernel is restarted and the code is re-run from the top (e.g., by a collaborator), it will raise an error.
* **dispersal**: _relevant_ code snippets may be spread across cells, and first need to be gathered to reproduce a cell output.
* **deletion**: relevant code may be accidentally deleted and old code versions overwritten during analysis or cleanup. This is especially pertinent to notebooks, where, e.g., persistent kernel memory may hide accidental deletion.

![The three types of messes in notebooks: disorder, dispersal, and deletion.](https://raw.githubusercontent.com/ETH-PEACH-Lab/UCPI-website/refs/heads/main/topics/img/messes.png)

Such _messes_ occur in most notebooks. For instance, nearly half of public notebooks on GitHub have cell disorder, i.e., the cells were executed in a different order than they are listed.

## Code Gathering and Automated Version Management

**Code Gathering** tries to address the data analyst's requirements through _automatic version management_; by keeping track of the order the code cells were executed (= scanning the _jupyter execution log_). This allows for a straightforward implementation of two features:

1. the user can select a result (= any code output, e.g., a plot), and the Code Gathering tool generates a **minimal snippet** that reproduces the result if run top to bottom in the provided order.
2. the user may then see the **result versions** for code cells that were executed multiple times, e.g., when a user may test different parameters for the same model.

![Minimal snippets and result versions provide portability and version management.](https://raw.githubusercontent.com/ETH-PEACH-Lab/UCPI-website/refs/heads/main/topics/img/features.jpg)

## Implications, Discussion, and Outlook

* **\[Version Management in Jupyter Notebooks]**: This work proposes one of the earliest approaches to "version management" in notebooks. Unlike in manual staging, like in more traditional git versioning, the developers' analysis progress is automatically tracked and used for both the **minimal snippet** as well as the **result versions** features. To this end, the authors drew much implementation inspiration from the related work around automated code refactoring and code walkthroughs in non-notebook coding environments and adapted it to the unique challenges arising from development in exploratory notebook development.
* **\[Challenges in End-to-End Jupyter Notebook Version Management]**: While this tool provides some foundational capabilities for version management for the rapid prototyping nature of juypter notebooks, it still leaves open questions about their end-to-end usage. For instance:
  * Although the minimal snippet feature is considered highly useful, the version management tool is less so, according to the user evaluation. This raises the questions: how can we design _better_ features for notebook version exploration beyond simply listing the changed snippets of code? And further, how do we make notebook versioning _scale_ to a more collaborative setting with multiple users or longer project edit histories?
  * Notebooks are still supposed to be _literate_ programming tools, so how can we properly handle markdown during the automatic cleanup process? Such cells are executed differently to code cells, and are currently ignored by the Code Gathering tools.
  * Finally, how does this integrate with other version management tools, like git?
* **\[Opportunities for Interactivity and Visualization for Versioning]**: The highlighted limitations of the Code Gathering tools show the potential for follow-up work that helps users better navigate result versioning. One future avenue of work is improving notebook diff visualizations across text, code, and plots on different granularities to help a user better understand and aggregate changes for notebooks with large edit histories. For instance, [Loops](https://doi.org/10.1109/TVCG.2024.3456186) proposes such compact and detailed diff widgets that help a user get a fast overview of notebook versions. Further, providing navigational guidance between versions is highly relevant to the issue of scale, and could potentially also be supported through interactive features such as intelligent semantic version grouping and search, improving on the ones implemented by [Verdant](https://marybethkery.com/Verdant/), a notebook provenance tool.

### Reading List

* [Code Gathering](https://dl.acm.org/doi/10.1145/3290605.3300500): Head, A., Hohman, F., Barik, T., Drucker, S. M., & DeLine, R. (2019, May). Managing messes in computational notebooks. In Proceedings of the 2019 CHI Conference on Human Factors in Computing Systems (pp. 1-12).
* [Code code evolution](https://doi.org/10.1145/3544548.3580997): Raghunandan, D., Roy, A., Shi, S., Elmqvist, N., & Battle, L. (2023). Understanding how people change data science notebooks over time. In Proceedings of the 2023 CHI Conference on Human Factors in Computing Systems (CHI ’23) (Article 863, pp. 1–12). Association for Computing Machinery.
* Rule, A. (2018). [Design and Use of Computational Notebooks](https://escholarship.org/uc/item/0dc498tf). UC San Diego. ProQuest ID: Rule\_ucsd\_0033D\_17498. Merritt ID: ark:/13030/m5fn63pf.
* [Verdant](https://marybethkery.com/Verdant/): Kery, M. B., John, B. E., O'Flaherty, P., Horvath, A., & Myers, B. A. (2019, May). Towards effective foraging by data scientists to find past analysis choices. In Proceedings of the 2019 CHI Conference on Human Factors in Computing Systems (pp. 1-13).
* [Loops](https://doi.org/10.1109/TVCG.2024.3456186): Eckelt, K., Gadhave, K., Lex, A., & Streit, M. (2024). Leveraging provenance and visualization to support exploratory data analysis in notebooks. IEEE Transactions on Visualization and Computer Graphics, 31(1), 1213–1223.
