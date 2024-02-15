---
title: "SELF-DISCOVER: Large Language Models Self-Compose Reasoning Structures"
categories:
  - Blog
---
SELF-DISCOVER is a new method that allows LLMs such as GPT-4 and PaLM 2 to autonomously construct their internal reasoning structures. This approach enhances LLMs' abilities to address complex reasoning tasks while achieving significant gains in performance.

## Method overview

The SELF-DISCOVER approach is inspired by the way humans draw on existing knowledge and skills to tackle new problems. When faced with a challenge, people naturally search their past experiences for relevant tools and strategies. Next, they apply those tools to the task at hand. Often, solving complex problems requires combining multiple skills and areas of knowledge.

SELF-DISCOVER has two-stages. An overview of the process can be seen here:

**Stage 1: Discovering the Reasoning Structure**

Given a task and a set of descriptions outlining high-level problem-solving strategies (e.g., "Use critical thinking," "Let's think step by step"), SELF-DISCOVER's first stage uncovers the most effective reasoning structure for the task. It uses three meta-prompts to guide the language model in selecting, customizing, and creating an actionable plan. This stage only needs to be performed once for each type of task. This stage consists of three actions:

- **Select** - choose the relevant reasoning modules for task-solving from the available set of reasoning module descriptors. The method uses a pre-defined set of 39 such descriptors
    
- **Adapt** - rephrase the selected descriptors to be more specific for the task
    
- **Implement** - create a structured actionable plan so that the task can be solved by following the structure
    

![](https://media.licdn.com/dms/image/D4E12AQFSu0DzIlvZXg/article-inline_image-shrink_400_744/0/1707771234902?e=1713398400&v=beta&t=4ISbGPRlUTi5GEPqAknpkRC8tZUNSCz3vgRqmTbEZlI)

The three actions for SELF-DISCOVER

Prompts for the three actions are shown below:

![](https://media.licdn.com/dms/image/D4E12AQFwN3_Jx4GHBg/article-inline_image-shrink_400_744/0/1707771400898?e=1713398400&v=beta&t=u8YSdjz5gRcgi1hC_6j-BVByY_ZNYWydpQSB__ShhaM)

Meta Prompts for the three actions of SELF-DISCOVER

**Stage 2: Applying the Reasoning Structure**

Once the reasoning structure is discovered, it can be applied to any instance of the same task. The model is instructed to follow the structure, filling in the necessary details to arrive at an answer. The reasoning structure is simply appended to the prompt.

## Results

The results look quite promising, SELF-DISCOVER bringing consistent boost on different benchmarks:

![](https://media.licdn.com/dms/image/D4E12AQFi7oQvMrLfWQ/article-inline_image-shrink_400_744/0/1707771657850?e=1713398400&v=beta&t=X7l0G1c9nFpE3cLoXc-wJmRu0UuWjaRvFAh9cN72GGU)

SELF-DISCOVER Results

## Conclusion

The SELF-DISCOVER framework demonstrates the efficacy of enabling Large Language Models (LLMs) to independently develop and apply task-specific reasoning structures. This approach, inspired by human problem-solving strategies, shows very promising results on multiple benchmarks. For more details, please consult the [full paper](https://huggingface.co/papers/2402.03620).

Congrats to the authors for their work!

Zhou, Pei et al. “Self-Discover: Large Language Models Self-Compose Reasoning Structures.” (2024).
