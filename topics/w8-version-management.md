# W8 - Version Management

<!-- ### *Version management applied to manage the messes of the rapid prototyping programming environments of Jupyter Notebooks.* -->

### *Code Gathering - Version management for dealing with the messes of rapid prototyping in Jupyter Notebooks.*


<!-- ## Introduction to Version Management -->

Using **version management** is standard practice in software development. Tools like `git` have many functionalities – branching, merging, reverting, ... -  that allow for effective collaboration through version control. In fact, many of us have previously written more or less exactly the following lines:

```
git add .
git commit -m "update"
git push
```

Version management has many benefits, such as easy collaboration, and tracing back or recovering older code versions, as shown in a typical development workflow illustrated below.


![Version management with git enables collaboration, traceability, and recoverability.](/topics/img/version-management.png)

The benefits of version management are not only relevant to large-scale productionalized codebases, but also coding environments that work on smaller scales, such as the messy, rapid prototyping and data analysis as frequently implemented in *jupyter notebooks*. This raises the following questions;

- What messes or conflicts may arise during such prototyping? Which ones may be addressed by version management?
- How can we adapt "traditional" version management to notebook development such that it addresses developer needs?
<!-- - How can automated version management help? -->

This blog post mainly discusses the 2019 CHI paper *Code Gathering: Managing messes in computational notebooks.* [1], and its broader impact around version management for computational notebooks.

## Messes in Notebooks

Developing code in jupyter notebooks is... a messy process. Getting to a final version may take many iterations of exploration, testing, and cleaning up during development.

<!-- When questioning data analysts about what they care about when organizing notebooks,  -->

![Version management with git enables collaboration, traceability, and recoverability.](/topics/img/notebook-development-smaller.gif)

It turns out that data analysts require support when cleaning up their notebooks to 

1. keep track of old versions of notebook code, and 
2. be able to have portable (minimal) snippets of code, which they can easily copy and re-use.

**But why are these things even hard?** To answer this, the authors first evaluate the issues that commonly arise when developing code for notebooks, which make the aforementioned goals generally difficult. Namely, they are:

- **disorder**: because of the [persistent jupyter kernel memory](https://hex.tech/blog/jupyter-kernel-overview/), code may be developed out of execution order. If the kernel is restarted and the code is re-run from the top (e.g., by a collaborator), it will raise an error.
<!-- ```python
import pandas as pd
print(df.columns)
pd.read_csv(...)
``` -->
- **dispersal**: *relevant* code snippets may be spread across cells, and first need to be gathered to reproduce a cell output.

- **deletion**: relevant code may be accidentally deleted and old code versions overwritten. This is especially pertinent to notebooks, where, e.g., persistent kernel memory may hide accidental deletion.

## Code Gathering and Automated Version Management

### Reading List

* [Verdant](https://marybethkery.com/Verdant/): Kery, M. B., John, B. E., O'Flaherty, P., Horvath, A., & Myers, B. A. (2019, May). Towards effective foraging by data scientists to find past analysis choices. In Proceedings of the 2019 CHI Conference on Human Factors in Computing Systems (pp. 1-13).\

* [Code Gathering](https://dl.acm.org/doi/10.1145/3290605.3300500): Head, A., Hohman, F., Barik, T., Drucker, S. M., & DeLine, R. (2019, May). Managing messes in computational notebooks. In Proceedings of the 2019 CHI Conference on Human Factors in Computing Systems (pp. 1-12).
