# Questions

**Question 1 on Beyond Computer Science and Economics Methodology 1 Behavioral Game Theory and Mechanism Design: Innovating Behavioral Game Theory Tools**

Analyze your experience with oTree, identifying pain points in behavioral game theory research. Review related literature and class discussions to understand experimental economics' goals. Propose a software solution that outperforms oTree in at least three aspects, enhancing strategic interaction studies. Highlight why these advancements are crucial. Submit a concise essay question answer (500 words max) with your analysis and proposals, backed by literature and class insights. Your innovative ideas can significantly contribute to experimental economics, addressing current limitations and paving the way for advanced research methodologies. 

In the analysis, you must provide at least one example of your personal experience in deploying the trust game using oTree, together with a screenshot.

**Question 2 Beyond Computer Science and Economics Methodology 2 Multi-agent Reinforcement Learning:  Advancing Multi-Agent Reinforcement Learning**

Delve into the limitations of current multi-agent reinforcement learning (MARL) frameworks, focusing on environment constraints and agent algorithm customizations. Choose a classic game (e.g., Prisoner's Dilemma, Battle of the Sexes, or the Trust Game) to illustrate these limitations. Describe the development process of a MARL agent for your selected game, detailing the definition of states, actions, and rewards grounded in fundamental behavioral assumptions. Your analysis should provide insights into overcoming MARL's current limitations, fostering advancements in the field. Submit a comprehensive report (500 words max) with your findings and proposals.

In the analysis, you must provide at least one example of your personal experience in endeavoring to deploy the gameplay using one of the MARL frameworks, together with a screenshot. 

**Question 3 Brainstorm your research idea by criticizing existing research: Critiquing and Expanding upon Existing Research**

Objective: The goal of this assignment is to engage critically with existing research in the field of federated learning, using the specific paper presented by the guest speaker as a primary example. Students will assess the paper's research questions, methodologies, and application scenarios and propose new research ideas addressing the identified limitations or gaps.

Instructions:

1. Summary of the Paper

Core Research Questions: Briefly summarize the paper's primary research questions. What is the main problem or challenge the paper seeks to solve or understand?
Methodologies: Describe the methods employed in the paper to address the research questions. Consider the approaches, models, or experimental designs used.
Application Scenarios: Outline the application scenarios discussed in the paper. How does the paper propose to apply its findings or solutions in real-world contexts?

2. Critique of the Research Question

Reflect on the research questions posed in the paper. Are there other more significant objectives or questions that could be more relevant or impactful in this context? Explain why these alternative questions or objectives might offer more value or insight.

3. Critique of the Methodology

Analyze the assumptions made in the paper regarding the strategic environment and behavioral foundations. Discuss whether these assumptions are justified or if they require more reasonable treatment. Suggest how the methodology could be improved or altered to address these concerns.

4. Critique of the Application Scenario

Evaluate the relevance and currency of the federated learning scenarios presented in the paper. With the rapid advancement in technology, consider whether there are more modern or advanced application scenarios that could be more effective in solving similar issues, such as blockchain, generative AI, other privacy-preserving technologies, or quantum computing.

5. Beyond Computer Science and Economics

Consider the role of bounded rationality in both human and AI agents within the context of the paper's findings. Propose how the results might change if the study incorporated participants with specific psychological heuristics or different versions of AI, such as ChatGPT.
You must provide a concrete example: Conduct a mini-experiment by interviewing a human subject not in our class about their perspective on the paper's scenarios or crafting prompts to ask ChatGPT and analyze its responses. Discuss how these insights could dramatically alter the paper's conclusions.

# Answers

**Question 1**

I think Otree is relatively easy to use, and is sufficient for most experiments. However, it has some downsides which can be improved upon. First, a well-known downside of Otree (Chan et al. 2019) is its lack of multi-tenancy, which means that there will be no data isolation if multiple users try to use the same software installation; second, while the installation process is relatively straightforward for people who have basic knowledge of Computer Science, the lack of a GUI interface in the experimental design still might make it difficult to use for some economists who lack the relevant training; finally, as we found in class, it has some OS dependencies which are Windows-unfriendly.

I think the solution would be to create a wrapper for Otree that not only includes a GUI which is understandable for non-professionals, but also multiple separate instantiations which can be independently operated by different experimenters, and a wizard that automatically handles the installation process which takes the OS into account. The benefit of creating a wrapper over writing the software all over is that experts who are well familiar with the underlying mechanisms can still use the app in the normal method, not just beginners who need the GUI and the wizard.

The GUI interface can be created with Tkinter, which is a Python package, lightweight and suitable across platforms, such that the entire code structure will remain largely undisturbed (no cross-language accommodations are needed). The different instantiations will be wrapped in functions which are separately executed in threads. In practice, they can not only be used by different experimenters, but also in cases which call for data separation in a single experiment (e.g., as suggested by Fréchette, Sarnoff, and Yariv (2022), Turkers and students often behave differently). 

The user journey flowchart is as shown in Figure 1, with appended parts highlighted and noted in blue.

![ECON](https://github.com/Rising-Stars-by-Sunshine/ECON206-Shiran-Yuan/assets/105504535/2f56e580-d0b7-45dd-8d34-f9232c581cda)

*Figure 1* User Journey Flowchart of the Improved Design

Shu Wing Chan, Steven Schilizzi, Md Sayed Iftekhar, and Raymond Da Silva Rosa. "Web-based experimental economics software: How do they compare to desirable features?." Journal of Behavioral and Experimental Finance23 (2019): 138-160.

Guillaume R. Fréchette, Kim Sarnoff, and Leeat Yariv. "Experimental economics: Past and future." Annual Review of Economics 14 (2022): 777-794.

**Question 2**

My Prisoner’s Dilemma implementation based on PettingZoo: [link](https://colab.research.google.com/drive/1gOy5Dm8pe_tIb7Uv9XTLmkslu8owHtLm?usp=sharing).

The cardinality of the action space is 2: COOP (cooperation) or DEFECT (defection). Unilateral defection (a.k.a. betrayal) offers 10 utility points, while bilateral cooperation and defection respectively offer 5 and 3 points. 

The implemented agent is simple, but already requires a significant amount of boilerplate code. Hence I consider that the main limitation of PettingZoo is its lack of modularity and too much redundancy. An improvement in terms of game theory-oriented applications would be the introduction of a simpler wrapper class which handles the choices, iterations, and learning process automatically, instead of having to rely on manual operation of the choices and a separately written learning procedure. For instance, for a small record space, a Q-value table could be directly inserted into the class as an attribute variable, followed by automatic updates via Bellman equations. Similarly, when the rewards are fixed, a tree with alpha-beta pruning could be embedded. Those will allow for easier training of the agents. Currently, not only are the boilerplate code distracting, the learning curve of the framework also seems steep, such that the implementation procedure is difficult to understand.

**Question 3**

1.  Summary of the Paper

Core Research Questions: The paper aims to create an incentive mechanism for federated learning which addresses the bias problem. 

Methodologies: The paper introduces a concept known as “randomized client participation,” in which payment to the clients (for incentivization) was tailored to each of the clients.

Application Scenarios: The experiment was conducted on a system where a laptop acted as a server, connected to 40 Raspberry Pi clients via a Wi-Fi Router. However, results of the paper are presumably applicable to any system which leverages federated learning.

2.  Critique of the Research Question

The research question is highly important from two perspectives. First, federated learning, the overall field of study is vital because currently new technologies including IoT and edge computing often require federated learning such that artificial intelligence can be applied in those scenarios. In addition, the question of bias itself is also attracting increasing attention due to sociopolitical factors as well as the increasing need for AI safety and alignment with human values. Hence, the question which the paper solves is valuable.

3.  Critique of the Methodology

The paper’s methodology is sound because it is theory-backed, and also because of the sufficient experimentation. The results align with the expected outcomes and suggest that the method put forward by the paper can effectively solve the problem. Furthermore, it demonstrates the practical advantages of eliminating bias, which is a good further justification of the research question. The methodology is also inspiring since it uses many concepts from game theory such as payment and incentive, therefore being a fundamental contribution to the field as well.

4.  Critique of the Application Scenario

The application scenario tested in the experiment is relatively representative of real-life scenes. In particular: Raspberry Pis are often used as standard clients, and Wi-Fi is often the data transmission protocol, so those two adequately describe a common usage scenario. As for the task, while MNIST and EMNIST may be relatively simple tasks, they also are high-quality datasets with few errors and hence distracting factors, and thus are also appropriate choices for a foundational piece of research like this.

5.  Beyond Computer Science and Economics

![Screenshot 2024-03-30 at 21 10 39](https://github.com/Rising-Stars-by-Sunshine/ECON206-Shiran-Yuan/assets/105504535/652aebfd-e206-46d5-93be-c8120cf1402b)

*Figure 2* Communciation with GPT 3.5

GPT 3.5, as shown in Figure 2, suggests that introducing bounded rationality into the mechanism might increase the system’s robustness and generalizability. In this case, the mathematical premises of the paper may no longer be applicable by design since, for instance, a client with a higher intrinsic value parameter could now also set a higher price on its information irrationally. This will degrade the system’s stability and interpretability, but meanwhile, there indeed might be, as GPT suggests, some benefits associated with this more human-like behavior.
