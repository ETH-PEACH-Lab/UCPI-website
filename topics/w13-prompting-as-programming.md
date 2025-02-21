---
description: 'Author: S. Pfisterer'
---

# W12 - Prompting as Programming

## **ChainForge: Making LLM Testing Accessible to Everyone**

By Samuel Pfisterer, a final year Computer Science undergraduate student at ETH Zurich.

Imagine you are a developer at a healthcare startup, building an AI assistant that helps doctors summarize patient records. One day, your AI starts leaking sensitive patient information when users include certain phrases in their requests. Your team needs to quickly determine which AI model and prompt combinations best prevent data leakage while maintaining functionality and testing hundreds of variations across multiple models to protect patient privacy.

This scenario highlights a critical challenge when working with Large Language Models (LLMs). For building healthcare assistants, financial advisors, or legal document processors, two questions are paramount: How do you systematically test your AI system's security and behavior? And how do you choose the right combination of model and prompts that balance security, performance, and cost?

### **The LLM Testing Challenge**

Systematic testing of LLM behavior remains surprisingly difficult. Current tools force developers to choose either to explore through chat interfaces one prompt at a time or to write complex code for systematic tests. It is like choosing between a microscope or telescope - when you need both.

Platforms such as [Vellum.ai](http://vellum.ai/) offer code-free interfaces, but limit testing to single prompts (Vellum AI, 2024). Academic tools such as PromptMaker (Jiang et al., 2022) lack evaluation capabilities, whereas others such as PromptAid (Mishra et al., 2023) focus on narrow use cases. Users need an end-to-end platform that enables both exploration and systematic evaluation without coding.

### **Enter ChainForge: Bridging Exploration and Evaluation**

ChainForge offers a unique solution: a visual platform for exploring possibilities and systematically evaluating them (Arawjo et al., 2024). Like a visual laboratory, it allows you to transition from exploration to rigorous testing by connecting simple "nodes"(Arawjo et al., 2024).

The system can simultaneously test multiple prompts across multiple models, enabling both informal exploration and systematic evaluation through four building blocks (Arawjo et al., 2024):

#### **Input Nodes**

Starting points for test data, prompts, and variables - like patient records and security-focused prompts (Arawjo et al., 2024).

#### **Generator Nodes**

Handle interactions with different AI models for quick and large-scale evaluation (Arawjo et al., 2024).

#### **Evaluator Nodes**

Analyze responses based on your criteria, such as checking for leaked patient data (Arawjo et al., 2024)].

#### **Visualizer Nodes**

Create graphs and visualizations to compare model-prompt combinations (Arawjo et al., 2024).

This flexible design allows developers to move seamlessly between exploration and systematic evaluation, without writing code (Arawjo et al., 2024). For healthcare applications, this means quickly finding the right balance between privacy protection and functionality.

### **From Testing to Real-World Impact**

ChainForge's journey revealed surprising applications far beyond its original design. With over 5,000 installations (Arawjo et al., 2024) and 2,400 GitHub stars (_Ianarawjo/ChainForge_, 2024), the tool has found its way into diverse real-world scenarios.

Consider a German consulting firm that uses ChainForge to evaluate local LLM providers for GDPR compliance. By comparing the responses of different models, they could assess which providers best protected sensitive data while maintaining performance (Arawjo et al., 2024). In another case, materials science researchers used it to test the models' understanding of polymer properties, systematically evaluating how well different LLMs could process technical information (Arawjo et al., 2024).

Most surprisingly, knowledge workers have adopted ChainForge as a data processing tool. They leveraged ChainForge's ability to run hundreds of prompt variations to process data at scale and transform raw information into structured formats through systematic LLM testing (Arawjo et al., 2024).

Through these real-world applications, three distinct patterns have emerged in how people approach LLM testing (Arawjo et al., 2024):

* They begin with rapid exploration, testing different prompts and models to understand what's possible
* Then move to systematic evaluation, setting up automated tests to validate their findings
* Finally, they refine their approach, optimizing prompts and templates for their specific needs

This progression from exploration to systematic testing reflects a maturing approach to LLM development, where initial experimentation leads to rigorous evaluation and optimization.

### **Challenges**

Although ChainForge has made LLM testing more accessible and unified exploration and systematic evaluation, several challenges remain:

* API key management creates friction, particularly for non-technical users working across multiple models. One possible solution might be that ChainForge can manage its own keys, and the user pays ChainForge.
* Cost tracking and optimization across different models are not possible using ChainForge. This could be added – other products have already done this (e.g., LangSmith).
* Limited support for the production deployment workflow. Other tools are tackling this (e.g., LangSmith)

### **Recent Progress and Industry Developments**

The LLM testing landscape has evolved rapidly since ChainForge's release.

#### **Commercial Platforms**

LangSmith (LangSmith, 2024) now offers integrated exploration and evaluation capabilities through the Prompt Canvas and systematic testing tools. Furthermore, LangSmith tackles some of ChainForge’s downsides, such as evaluating during production or evaluating costs.

OpenAI (OpenAI, 2024) has released its internal evaluation framework (Evals) to help standardize the prompt/model evaluation with no code required. This tool is still in its beta, but shows a clear trend that evaluation features have become a standard among LLM tooling/foundational model providers.

#### **Research Advances**

Automatic prompt optimization tools, such as Promptim (LangChain, 2024), are emerging to help automatically improve prompts.

AI assistants such as ChainBuddy (Zhang & Arawjo, 2024) help users overcome the "blank page problem" in setting up evaluation pipelines on ChainForge with simple natural language. For example, if you want to test which prompts work best to not return answers with sensitive data, you could simply ask this in a chat interface, and ChainBuddy sets everything up automatically.

### **Looking Forward**

The landscape of LLM testing continues to evolve rapidly. Two promising directions are emerging:

**Automation and AI Assistance**

Tools are moving beyond visual interfaces toward automated optimization. While ChainBuddy (Zhang & Arawjo, 2024) helps create evaluation pipelines through natural language interaction, systems like Promptim (LangChain, 2024) explore automatic prompt optimization. This suggests a future where users might simply describe their goals and let AI systems handle both pipeline creation and prompt refinement.

**Beyond Text**

The principles of systematic evaluation could extend beyond text to testing image generation, voice synthesis, and agent behavior.

While automation promises to make LLM testing more accessible, maintaining human oversight might remain crucial as these tools evolve. The goal could become to augment human judgment with AI assistance, not replace it entirely.

### References

Arawjo, I., Swoopes, C., Vaithilingam, P., Wattenberg, M., & Glassman, E. L. (2024). ChainForge: A visual toolkit for prompt engineering and LLM hypothesis testing. https://doi.org/10.1145/3613904.3642016

ianarawjo/ChainForge. (2024). https://github.com/ianarawjo/ChainForge

Jiang, E., Olson, K., Toh, E., Molina, A., Donsbach, A., Terry, M., & Cai, C. J. (2022). PromptMaker: Prompt-based prototyping with large language models. ACM. https://dl.acm.org/doi/10.1145/3491101.3503564

LangChain. (2024, November 13). Promptim: An experimental library for prompt optimization. LangChain Blog. https://blog.langchain.dev/promptim/

LangSmith. (2024). https://smith.langchain.com/

Mishra, A., Soni, U., Arunkumar, A., Huang, J., Kwon, B. C., & Bryan, C. D. B. (2023). PromptAid: Prompt exploration, perturbation, testing and iteration using visual analytics for large language models. [arXiv.org](http://arxiv.org/), abs/2304.01964. https://doi.org/10.48550/arXiv.2304.01964

OpenAI. (2024, November). https://openai.com/

Vellum AI. (2024). https://www.vellum.ai/

Zhang, J., & Arawjo, I. (2024). ChainBuddy: An AI-assisted agent system for helping users set up LLM pipelines. Association for Computing Machinery, 1–3. https://doi.org/10.1145/3672539.3686763
