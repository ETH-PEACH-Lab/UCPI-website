# W12 - Scaling Feedback for Programming Learners

## Revolutionizing Programming Classrooms: Scalable Feedback Through AI and Visualization

Discover how language models and visualization tools are reshaping the way instructors engage with students, making programming education more scalable, impactful, and learner-centric.

By [Xiaotian Su](https://xiaotiansu.github.io/), a first-year PhD student in PEACH lab at ETH Zurich, working on building AI-assisted tools for instructors and learners in programming education.

As programming classrooms continue to expand—both in physical size and across online platforms—the challenge of supporting large-scale learning environments becomes increasingly urgent. For example, introductory computer science courses at institutions like UC Berkeley and the University of Washington regularly enroll over a thousand students per term [7]. This growth poses a challenge for educators: how to provide timely, personalized, and meaningful feedback to students who need help. Traditional methods, such as addressing students who raise their hands, are effective in smaller settings but falter when scaled to classes of hundreds or more. Over the years, innovative tools have emerged to help instructors manage this complexity. More recently, the advent of Large Language Models (LLMs) has ushered in transformative changes in how feedback can be generated, delivered, and scaled. This blog explores how these advancements are empowering educators to reimagine their roles and create new opportunities for engaging learners.

### Classroom 1.0: code clustering and monitoring students' progress in real-time
Before the advent of generative models, researchers explored ways to manage and analyze students' programming solutions at scale, focusing primarily on clustering techniques for massive classes. For instance, **OverCode** utilized both static and dynamic analysis to cluster similar solutions, enabling instructors to further refine and group thousands of solutions based on various criteria [1]. However, it was primarily designed for post-hoc analysis, lacking real-time feedback capabilities and the means to monitor students' progress over time.

Building on the need for real-time support, **Codeopticon** introduced an interface allowing programming tutors to monitor a few hundred learners simultaneously and chat with them in real-time [2]. At a glance, tutors could observe how learners were editing and debugging their code and identify errors encountered. Despite its innovative approach, scaling feedback remained a challenge, as instructors still had to individually review each student's code.

To address these challenges, **VizProg** was developed to provide a more scalable and intuitive real-time visualization tool. It represented students’ statuses as a 2D Euclidean spatial map, encoding their problem-solving approaches and progress [3]. This visualization allowed instructors to explore both the temporal and structural evolution of students’ code and identify opportunities for feedback. However, the tool's scalability was limited, it can be applied to around 100 to 200 solutions; instructors found it overwhelming when a large number of students began working simultaneously. Moreover, understanding specific content often required manually selecting areas and examining raw code.

### Classroom 2.0: enpowering instructors with AI-driven insights
With the rise of LLMs, researchers have started leveraging these technologies to overcome the limitations of earlier tools. **CFlow**, for example, utilized LLMs for post-hoc analysis by generating line-level error information for student code [4]. By providing semantic-label abstractions and a color-coded histogram, it helped instructors identify common mistakes more efficiently when presented with over 6,000 submissions. Similarly, **VizGroup** harnessed LLMs to recommend event specifications, enabling instructors to monitor key correlation patterns between collaboration metrics and coding tasks for over 100 submissions in real-time [5]. Beyond these, tools like **SPHERE** directs instructors’ attention to critical student issues, offers guided control over LLM-generated feedback, and employs visual scaffolding to enhance feedback verification and quality [6]. These innovations illustrate how the integration of LLMs is transforming the way instructors interact with student solutions, making feedback and analysis more scalable and actionable.

Interestingly, all the tools mentioned above were designed specifically for introductory programming courses and evaluated primarily using Python-based datasets. Looking ahead, there is a pressing need to expand these innovations to cater to a broader range of programming topics, such as web development, data science, and other specialized areas. Additionally, future tools should address the diverse needs of learners across different experience levels, including intermediate and advanced programmers, to ensure more comprehensive and inclusive support in programming education.

### From overwhelmed to empowered: How can AI become the co-educator?
As we look ahead, the next frontier for programming education lies in creating an ecosystem where AI transcends its role as a mere assistant to become a true co-educator. This vision demands a shift from tools that provide one-off solutions to those that foster dynamic, ongoing collaboration between instructors, learners, and AI systems.

#### Balancing Automation and Autonomy
A key challenge in designing such systems is striking the right balance between automation and autonomy. While fully automated feedback mechanisms powered by LLMs can scale effortlessly to large classrooms, they risk oversimplifying nuanced pedagogical needs. On the other hand, systems that rely heavily on instructor input may fail to address the scalability issues they are meant to solve. The ideal solution lies in hybrid approaches: leveraging AI to handle routine tasks, such as identifying syntax errors or generating initial feedback drafts, while giving instructors the flexibility to refine and customize these outputs to suit individual learners' needs.

#### Creating a Feedback Loop Between AI and Educators
The long-term vision for programming classrooms involves establishing a symbiotic feedback loop where AI systems learn from instructors just as instructors benefit from AI insights. For example, instructors could provide the AI with detailed annotations or examples of effective feedback, such as suggesting alternative coding strategies to encourage creativity or asking probing questions to foster deeper collaboration among learners working in groups. These annotations might highlight when feedback should focus on enhancing problem-solving skills, encouraging innovative approaches, or building teamwork dynamics rather than merely correcting syntax or logical errors. Over time, the AI could analyze patterns in this instructor-provided feedback to refine its models, learning to prioritize actionable insights that inspire learners to explore diverse solutions, communicate more effectively, and engage in meaningful collaboration. This iterative process ensures the AI not only adapts to educators' evolving pedagogical strategies but also complements their expertise by amplifying the aspects of teaching that promote a richer, more interactive learning environment.

In the future, AI does not replace instructors but amplifies their ability to teach effectively and creatively. Together, instructors and AI co-educators can create a learning environment that is scalable, adaptive, and profoundly impactful.

### References

[1] Glassman, E. L., Scott, J., Singh, R., Guo, P. J., & Miller, R. C. (2015). OverCode: Visualizing variation in student solutions to programming problems at scale. _ACM Transactions on Computer-Human Interaction (TOCHI)_, _22_(2), 1-35.

[2] Guo, P. J. (2015, November). Codeopticon: Real-time, one-to-many human tutoring for computer programming. In _Proceedings of the 28th Annual ACM Symposium on User Interface Software & Technology_ (pp. 599-608).

[3] Zhang, A. G., Chen, Y., & Oney, S. (2023, April). VizProg: Identifying misunderstandings by visualizing students’ coding progress. In _Proceedings of the 2023 CHI Conference on Human Factors in Computing Systems_ (pp. 1-16).

[4] Zhang, A. G., Tang, X., Oney, S., & Chen, Y. (2024, July). CFlow: Supporting Semantic Flow Analysis of Students' Code in Programming Problems at Scale. In _Proceedings of the Eleventh ACM Conference on Learning@ Scale_ (pp. 188-199).

[5] Tang, X., Wong, S., Pu, K., Chen, X., Yang, Y., & Chen, Y. (2024). VizGroup: An AI-Assisted Event-Driven System for Real-Time Collaborative Programming Learning Analytics. _arXiv preprint arXiv:2404.08743_.

[6] Tang, X., Wong, S., Huynh, M., He, Z., Yang, Y., & Chen, Y. (2024). SPHERE: Scaling Personalized Feedback in Programming Classrooms with Structured Review of LLM Outputs. _arXiv preprint arXiv:2410.16513_.

[7] How big is UC Berkeley's biggest class? (n.d.). The Daily Californian. Retrieved December 25, 2024, from https://www.dailycal.org/archives/how-big-is-uc-berkeleys-biggest-class/article_def82e86-1d71-5d42-a070-f161580fd19c.html
