---
title: "In-Context Principle Learning from Mistakes"
categories:
  - Blog
---
In-context learning (ICL or _few-shot prompting_) it's one of the most widely used methods for adapting LLMs to downstream tasks, by learning from just a few input-output examples. In this paper, the authors introduce LEAP (Learning Principles). The goal is to learn _more_ from this few examples. In order to achieve this, the model learns task-specific **principles** that allow a better performance on new unseen questions. Below you can see some examples of learned principles:

![](https://media.licdn.com/dms/image/D4E12AQFudP9KOhy7RA/article-inline_image-shrink_400_744/0/1707689474472?e=1713398400&v=beta&t=Ub8nWw7G846DNtXUSrOHaYmKClPiFwTON7Z_jqRCNHI)

Examples of learned principles

### Method overview

LEAP takes a different approach than most in-context learning (ICL) methods where the models are given correct examples of how to do a task in the prompt. LEAP does something unique:

1. **Intentional Mistakes:** LEAP starts by showing the language model examples with mistakes on purpose.
    
2. **Principle learning:** The model then compares the wrong answers to the right ones to figure out general rules about what not to do.
    
3. **Inference with learned principles:** Finally, LEAP uses both the examples and the principles it learned to answer new questions it hasn't seen before.
    

![](https://media.licdn.com/dms/image/D4E12AQEHHlJRGbCBXA/article-inline_image-shrink_1000_1488/0/1707689556230?e=1713398400&v=beta&t=1HqvBKWljyD9Vdp2gV5WVDXl7yGoN8aezgoWkD-taLA)

LEAP process: Step 1 - Generate mistakes; Step 2 - Learn principles from mistakes; Step 3 - Use principles at inference.

For mistake generation, the authors use a zero-shot chain-of-thought prompt in order to generate 15 possible outputs with non-zero temperature. From these outputs, the _incorrect_ responses are identified and used to generate principles. For principle generation, the used prompt is shown below:

![](https://media.licdn.com/dms/image/D4E12AQEuSM1w6rqeKQ/article-inline_image-shrink_400_744/0/1707690234327?e=1713398400&v=beta&t=F78oGWelxmP-oFjcLtDTS4iNm8CqVLTCV4yqSyQsOI0)

Principle generation prompt

These insights are aggregated into a set of **low-level principles**. Finally, given these low-level principles, the LLM is asked to condense them into 5 key bullet points that are denoted as **high-level principles**. Now, that the principles are generated, both low-level and high-level ones can be used at inference on unseen new questions. The authors make a comparison on performance between concatenating to the prompt low-level or high-level principles.

### Results

The utility of LEAP has been validated across various benchmarks, including tasks that necessitate mathematical reasoning and textual reasoning. LEAP boosts the performance of advanced models such as GPT-3.5-turbo, GPT-4, Claude-2 or Gemini Pro across these domains. Below you can see the results in both cases (with low-level principles or high-level ones) along with some qualitative examples:

![](https://media.licdn.com/dms/image/D4E12AQF3t4fe1WX8KA/article-inline_image-shrink_400_744/0/1707690738324?e=1713398400&v=beta&t=sXb3JdbGnsP9M3lgkJXgGKzew2K-9EB_ybvUcw4fqXg)

Results on HotpotQA and DROP

![](https://media.licdn.com/dms/image/D4E12AQEDcdfHQlEcDg/article-inline_image-shrink_400_744/0/1707690794370?e=1713398400&v=beta&t=OhMCdeB728gwFBNmICUcx3qfkESiw_0Mn8LwFjmagiM)

Results on GSM8K and MATH

![](https://media.licdn.com/dms/image/D4E12AQGXn0YkfMcJnw/article-inline_image-shrink_400_744/0/1707691221599?e=1713398400&v=beta&t=G9fMbM65UUNMQM88AL_2fULKVJ-6Wre-F0LUd3U3i9E)

Qualitative examples

### Conclusion

LEAP introduces a significant advancement in the training and application of LLMs by using a mechanism for learning from errors and defining principles to avoid the errors. These principles are then used at inference by feeding them to the model in order to boost the accuracy on unseen new examples. For more details please consult the [full paper](https://huggingface.co/papers/2402.05403).

Congrats to the authors for their work!

Zhang, Tianjun et al. “In-Context Principle Learning from Mistakes.” (2024).
