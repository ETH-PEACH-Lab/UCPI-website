# Accessible Programming Environments for Visually Impaired Developers

A significant percentage of the world’s population experiences visual impairment, with estimations for moderate to severe impairment 
being around 5 percent of the world population, and much higher rates for mild impairment. (Bourne et al., 2020)
This group seems to be underrepresented in the programming profession, which is understandable given that most development environments rely heavily on visual interaction.
This blog post summarizes past efforts to improve the accessibility of development environments for visually impaired (VI) developers and explores opportunities for future work in this field.

## Introduction

Visually impaired developers typically interact with development environments through screen readers — tools that read screen contents aloud,
or braille displays that provide tactile text representations. (Potluri et al., 2018)
However, these tools depend on proper support from the environment, such as accurately labeled buttons and accessible layouts.
Beyond this requirement, several other challenges make this interaction less effective.

Potluri et al. identify four main challenges for VI developers: **Discoverability**, **Glanceability**, **Navigability**, and **Alertability**: 

- **Discoverability** refers to the ability to find new or hidden features, enabling users to improve their proficiency with an IDE over time.
- **Glanceability** is the ability to quickly absorb multiple streams of information at a glance. Notable examples are getting an overview of source code or seamlessly switching between windows like source code, console, and file explorers.
- **Navigability** focuses on moving efficiently within the source code. Sighted developers can scroll and click while keeping awareness of the surrounding context. For VI developers, navigation is often restricted to line-by-line moving, since screen readers only read the currently active line.
- **Alertability** involves proactive communication of information by the IDE, such as syntax errors or debugging states. For VI developers, screen readers rarely provide these cues effectively, leading to an information gap.

(Potluri et al., 2018)

Mountapmbeme et al. also highlight **code editing** as a challenge. VI developers often lose context when editing code inline, leading them to favor out-of-place editing approaches,
that is copying text to a separate window and edit it there before copying it back. (Mountapmbeme et al., 2022)

## Example projects

Many projects have aimed to address these challenges through new tools and interfaces.

**StructJumper** a plugin for Eclipse, tries to improve navigability and glanceability by representing source code as a tree rather than plain text.
This tree structure, similar to an outline view, enables developers to navigate between parent and child nodes. 
Nodes are classes, functions, blocks (such as if statements) and code blocks. (Baker et al., 2015)

**CodeTalk** later did a similar plugin for Visual Studio, they however heavily extended the functionality. Apart from an accessible tree view of the code,
they added “Talk Points”, audio-based breakpoints that notify developers without breaking execution, proactive syntax error notifications via sound, 
and an accessible error list for quick navigation. They also added a feature to get the context of the current line. (Potluri et al., 2018)

The **Grid-Coding** IDE finally adopts a grid-based representation of code. Each cell corresponds to a code segment or indentation level, 
enabling VI developers to comprehend and edit code more intuitively without losing focus. Similarly to Codetalk users are notified
about syntax errors via audio cues. (Ehtesham-Ul-Haque et al, 2022)

An entirely different approach is taken by papers like TangibleGrid or Tactile Code Skimmer. 
Instead of essentially replacing the screen with audio output, they provide specialized tangible input devices.

**TangibleGrid** allows developers to design web pages using a physical board where “brackets” (expandable rectangles) are placed to create layouts.
The placements of the brackets on the board are detected and translated into a corresponding website. (Li et al, 2022)

**Tactile Code Skimmer** introduces a device with sliding tactors that represent the structure of code in a tangible fashion.
Developers can feel the code’s structure and navigate to specific lines using onboard navigation buttons. The tactors either represent
code line by line, or indentation level by indentation level.(Falase et al, 2019)

## Future Work

While there has been a lot of innovative work on providing better user interfaces via plugins or specialized devices, a significant drawback seems to be the maintenance of the developed tools.
Codetalk for example is only usable with VS 2015, and similarly, StructJumper seems to not be available publicly.
Tangible interfaces on the other hand require specialized hardware that can be expensive and difficult to obtain in the first place.

A promising direction for future work could potentially focus on enhancing screen readers themselves, rather than providing highly specialized tools.
Advances in machine learning offer the potential to create intelligent screen readers capable of describing on-screen content contextually,
rather than simply reading out text or accessibility labels. 
Such systems could adapt dynamically to the fast evolution of development environments and programming languages, providing a more maintainable solution for VI developers.

## References

Baker, C.M., Milne, L.R., & Ladner, R.E. (2015). StructJumper: A Tool to Help Blind Programmers Navigate and Understand the Structure of Code. *Proceedings of the 33rd Annual ACM Conference on Human Factors in Computing Systems.*

Bourne, R. R., Steinmetz, J., Flaxman, S., Briant, P. S., Taylor, H. R., Resnikoff, S., Casson, R. J., Abdoli, A., Abu-Gharbieh, E., Afshin, A., Ahmadieh, H., Akalu, Y., Alamneh, A. A., Alemayehu, W., Alfaar, A., Alipour, V., Anbesu, E., Androudi, S., Arabloo, J., ... Vos, T. (2020). Trends in prevalence of blindness and distance and near vision impairment over 30 years: An analysis for the Global Burden of Disease Study. *The Lancet Global Health*, 9, e130-e143. https://doi.org/10.1016/S2214-109X(20)30326-1

Ehtesham-Ul-Haque, M., Monsur, S.M., & Billah, S.M. (2022). Grid-Coding: An Accessible, Efficient, and Structured Coding Paradigm for Blind and Low-Vision Programmers. *Proceedings of the 35th Annual ACM Symposium on User Interface Software and Technology.*

Falase, O., Siu, A.F., & Follmer, S. (2019). Tactile Code Skimmer: A Tool to Help Blind Programmers Feel the Structure of Code. *Proceedings of the 21st International ACM SIGACCESS Conference on Computers and Accessibility.*

Li, J., Yan, Z., Jarjue, E., Shetty, A., & Peng, H. (2022). TangibleGrid: Tangible Web Layout Design for Blind Users. *Proceedings of the 35th Annual ACM Symposium on User Interface Software and Technology.*

Mountapmbeme, A., Okafor, O., & Ludi, S. (2022). Addressing accessibility barriers in programming for people with visual impairments: A literature review. *ACM Trans. Access. Comput.*, 15(1), Article 7. https://doi.org/10.1145/3507469

Potluri, V., Vaithilingam, P., Iyengar, S., Vidya, Y., Swaminathan, M., & Srinivasa, G. (2018). CodeTalk: Improving Programming Environment Accessibility for Visually Impaired Developers. *Proceedings of the 2018 CHI Conference on Human Factors in Computing Systems*.
