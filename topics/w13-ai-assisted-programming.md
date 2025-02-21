---
description: 'Author: S. Bohl'
---

# W12 - AI-Assisted Programming

## **Speaking the Language of AI: How to Close the Communication Gap with Code-Generating Models**

By Samuel Bohl, Computer Science Master’s Student at ETH Zurich

Bio: Samuel is pursuing a major in Database Management and a minor in Machine Intelligence. His interest in this particular topic stems from hands-on experience using various AI tools to enhance productivity in his work as a software engineer.

## Introduction

Imagine this: You ask an AI to “analyze my astronaut mission data,” and it generates perfect code, except it calculates mission length by counting commas instead of dates. Frustrating, right? This is the reality of programming with large language models (LLMs) today. While tools like GitHub Copilot and ChatGPT have democratized coding, a critical problem remains: How do we teach users to “speak AI” so their intentions translate into accurate code?

Recent research reveals a promising solution: grounded abstraction matching. But to understand why this matters, let’s rewind to a fundamental truth: AI doesn’t “understand” you, it just predicts words. Bridging this gap could be the key to unlocking natural language programming’s true potential.

## From Sci-Fi Fantasy to Everyday Tool

The idea of talking to computers in plain English isn’t new. In the 1980s, AppleScript let users automate tasks with "quasi" English commands—if you could stomach its rigid syntax. Fast-forward to 2023: LLMs like GPT-4 can turn vague prompts like “make a website with a blue button” into functional code. But here’s the catch: flexibility breeds unpredictability.

As a student experimenting with Codex, I’ve seen this firsthand. Ask it to “sort a list of planets by size,” and it might use `order_by=radius`—or `order_by=distance_from_Sun` if it hallucinates. The AI isn’t being stubborn; it’s struggling to map your words to programming concepts. This is what researchers call the abstraction gap: the mismatch between how humans describe tasks and how code implements them.

## Why “Just Add Examples” Doesn’t Work

Early solutions like tutorials or rigid templates fail because they ignore how humans naturally learn. Take Microsoft’s Clippy: it forced users to memorize specific phrases, leading to frustration (Luger & Sellen, 2016). This approach creates brittle mental models. For instance, teaching someone to type “calculate average” leaves them lost when they need to “compute median temperature.” Templates also ignore context “Sort \[column] by \[criteria]” works until you need to sort multiple columns with custom rules. Worse, they stifle creativity, trapping users in a “vocabulary cage” where they’re afraid to deviate from approved phrases.

This is why early users of tools like GitHub Copilot felt like they were “guessing lottery numbers” (Sarkar et al., 2022). Grounded abstraction matching solves this by teaching users how the AI thinks, not just what to say.

## Grounded Abstraction Matching: Teaching AI to Speak _Your_ Language

Let’s break down this jargon. Imagine you’re a scientist analyzing astronaut mission data. You type:

> “Calculate average mission length.”

Instead of just generating code, the AI responds:

> “To do this, I’ll create a ‘Mission Length’ column by dividing ‘Space Flight Hours’ by the number of commas in ‘Missions’ plus one.”

This response does two key things: First, it grounds the abstraction. It explicitly links your goal (“average mission length”) to code operations (column creation, string parsing). Secondly, it teaches through examples: Next time, you might ask, “Compute total training hours per comma separated mission.”

Liu et al. (2023) call this a bidirectional feedback loop. Users learn which phrases trigger reliable code (e.g., “count commas” vs. “count items”), while the AI adapts to their vocabulary. It’s like having a patient tutor who says, “Here’s how I’d phrase that.”

## Why This Matters for the Future of Programming

Grounded abstraction matching doesn’t just improve code quality, it transforms how users interact with AI. In Liu et al.’s study, users who received grounded feedback improved their success rates dramatically. They began selfcorrecting, generalizing patterns, and tackling complex tasks with confidence.

This mirrors how children learn language through pragmatic inference, not by memorizing rules, but by seeing how words create results (Bender & Koller, 2020). For example, when an AI explains that “calculate average” maps to `SUM()/COUNT()`, users intuitively grasp that “find typical value” might need `MEDIAN()`.

This has several potential implications. In healthcare, nurses could learn to specify thresholds when flagging abnormal readings. In education, students might clarify whether “plot historical trends” means bar charts or line graphs. And in finance, analysts could intuit that “forecast Q3 sales” requires seasonal context.

Ultimately, this approach democratizes computational thinking. Users learn not just to use AI, but to collaborate with it. Future interfaces might even detect abstraction gaps in realtime, asking, “You said ‘analyze sales trends’ - should I compare monthly averages or detect unusual spikes?” This isn’t about simplifying programming; it’s about creating a shared language where humans and AI grow smarter together.

## Beyond Code: A Blueprint for Human AI Collaboration

The lessons here extend far beyond programming. Consider healthcare: A doctor asking an AI to “identify high risk patients” might need to learn that specifying “age > 65, LDL > 190” yields better results. As Kocielnik et al. (2019) note, adjusting user expectations is critical for AI adoption.

But there’s a deeper question: Should we mold humans to speak AI, or vice versa? I argue for a middle path. Future interfaces might: Detect abstraction gaps: “You said ‘analyze sales trends’. Did you mean monthly averages or anomaly detection?” or Personalize over time: Learn that you use “total” for summing columns and “combine” for merging datasets.

## The Road Ahead: From Copilots to Collaborators

As an AI enthusiast, I’m torn between excitement and caution. Yes, GPT-4 etc. can write code, but collaborating with AI requires a shared language, one that respects both human intuition and computational precision.

The future won’t eliminate programming languages, just as calculators didn’t kill arithmetic. Instead, we’ll see a new literacy emerge: the ability to guide AI with clarity and critique its output. Grounded abstraction matching is a first step toward this future, where AI doesn’t just answer questions but helps us ask better ones.

### References

* Bender, E. M., & Koller, A. (2020). Climbing towards NLU: On Meaning, Form, and Understanding in the Age of Data. In Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics, 5185-5198.
* Brown, T. B., Mann, B., Ryder, N., Subbiah, M., Kaplan, J., Dhariwal, P., ... & Amodei, D. (2020). Language Models are Few-Shot Learners. arXiv preprint arXiv:2005.14165.
* Kocielnik, R., Amershi, S., & Bennett, P. N. (2019). Will you accept an imperfect AI? Exploring designs for adjusting end-user expectations of AI systems. In Proceedings of the 2019 CHI Conference on Human Factors in Computing Systems, 1-14.
* Liu, M. X., Sarkar, A., Negreanu, C., Zorn, B., Williams, J., Toronto, N., & Gordon, A. D. (2023). "What It Wants Me To Say": Bridging the Abstraction Gap Between End-User Programmers and Code-Generating Large Language Models. In Proceedings of the 2023 CHI Conference on Human Factors in Computing Systems, 1-31.
* Luger, E., & Sellen, A. (2016). "Like Having a Really Bad PA": The Gulf between User Expectation and Experience of Conversational Agents. In Proceedings of the 2016 CHI Conference on Human Factors in Computing Systems, 5286-5297.
* Sarkar, A., Gordon, A. D., Negreanu, C., Poelitz, C., Ragavan, S. S., & Zorn, B. (2022). What is it like to program with artificial intelligence? arXiv preprint arXiv:2208.06213.
