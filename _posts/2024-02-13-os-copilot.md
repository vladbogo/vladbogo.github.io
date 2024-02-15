---
title: "OS-Copilot: Towards Generalist Computer Agents with Self-Improvement"
categories:
  - Blog
---
OS-Copilot is a new framework that introduces a method for creating general-purpose computer agents with enhanced capabilities and adaptability. It aims to facilitate the development of agents that can effectively interact with various operating system components, performing a wide range of tasks, from navigating files and executing code to handling multimedia content. The framework's effectiveness is demonstrated through the performance of its agent, FRIDAY, on the GAIA benchmark, surpassing existing methods and showcasing its ability to learn and accumulate skills in unfamiliar environments.

## Overview

![](https://media.licdn.com/dms/image/D5612AQGuQmirbsWm5Q/article-inline_image-shrink_400_744/0/1707859898044?e=1713398400&v=beta&t=zro8bB_SiP6jMo8_ZzjhyXqdNDHoYfDZ0bTKEbf_XLQ)

OS-Planner overview

When OS-Copilot receives a user request, a planner first constructs a plan that decomposes the request into subtasks. Given a subtask, the configurator maintains a working memory that is responsible for retrieving tools, knowledge, and any other relevant information needed for task completion. Based on the information provided by the configurator, the actor will iteratively perform operations of execution and criticism until the subtask is completed. In particular, the criticism operation involves collecting execution feedback for self-correction and improvement. Now let's see more details about each component.

### Planner

Focuses on interpreting user requests and decomposing complex tasks into simpler subtasks. It employs advanced planning methodologies, including a directed acyclic graph-based planner, to optimize task execution by enabling parallel processing of independent tasks. Each node corresponds to a subtask and the links represent the interdependencies between tasks.

### Configurator

Adjusts subtasks for execution, drawing inspiration from human memory systems. It includes:

- **Declarative Memory**: Stores user preferences and semantic knowledge to personalize interactions and inform decision-making.
    
- **Procedural Memory**: Contains a repository of tools for translating commands into executable actions, enhancing the agent's interaction with the operating system.
    
- **Working Memory**: Facilitates short-term information processing, connecting planning, configuration and execution phases by managing information flow and task updates.
    

### Actor

Executes tasks and evaluates outcomes through two stages:

- **Executor**: Generates and executes commands or actions based on the configured prompts, leveraging the framework's diverse runtime environments.
    
- **Critic**: Assesses task completion, identifies execution errors, and suggests adjustments, ensuring tasks are executed accurately and efficiently.
    

Each component is designed to enhance the agent's ability to understand, plan, and execute tasks autonomously, demonstrating the framework's comprehensive approach to building advanced digital assistants.

## The FRIDAY agent

A distinctive feature of FRIDAY is its self-improvement mechanism, which allows it to autonomously expand its operational capabilities across new applications. This is achieved through a self-directed learning approach, wherein FRIDAY identifies and engages in tasks that facilitate the acquisition of new skills and knowledge. Self-directed learning is instrumental in FRIDAY's development, enabling the agent to formulate and execute tasks that align with specific learning objectives. Here's an example where the agent generates a Python script that utilizes Apple Script in order to "Changes the system into Dark mode":

![](https://media.licdn.com/dms/image/D5612AQG-j6hUA2mU-A/article-inline_image-shrink_400_744/0/1707860703159?e=1713398400&v=beta&t=tBgW-2MJKMwDIvc3nMd7YysU8Zkvv2qdjRgRj7EFC0M)

FRIDAY example

## Results

FRIDAY's capabilities are measured on the GAIA benchmark. To answer questions in GAIA, computer agents need skills to calculate numbers, browse the web, process video and speech signal, and manipulate files, etc. Here are the results:

![](https://media.licdn.com/dms/image/D5612AQHQo7r9Nup8GA/article-inline_image-shrink_400_744/0/1707860889819?e=1713398400&v=beta&t=Ul3jrYiRXGf6QIrB0e3YAGjFIOumuJNha8vq6PjmPhs)

Results on the GAIA benchmark

## Conclusion

OS-Copilot and FRIDAY represent a new step toward creating smart, self-improving agent/llms helpers. FRIDAY shows very promising results in solving open-environment computer tasks, and demonstrating its capability to effectively learn and control previously unseen applications. For more details please consult the [full paper](https://huggingface.co/papers/2402.07456).

**Other resources**:

Code: [https://github.com/OS-Copilot/FRIDAY](https://github.com/OS-Copilot/FRIDAY)

Project page: [https://os-copilot.github.io](https://os-copilot.github.io/)

Congrats to the authors for their work!

Wu, Zhiyong et al. “OS-Copilot: Towards Generalist Computer Agents with Self-Improvement.” (2024).
