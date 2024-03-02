---
title: "A Closer Look at the Limitations of Instruction Tuning"
categories:
  - Blog
---
In this paper, the authors investigate the efficacy of Instruction Tuning (IT) in Large Language Models (LLMs) for conversational agents. Instruction Tuning represents the process of training large language models (LLMs) using instruction-response pairs and is the widely used method for transforming base pre-trained LLMs into conversational agents. The goal of this work is to uncover limitations of instruction tuning through a series of experiments, focusing on how these limitations affect the performance and capabilities of LLMs.

## Overview

The authors employ a mixed-method approach for evaluation and design a comprehensive set of experiments that allow for an in-depth analysis of IT's impact across various dimensions, including knowledge retention, hallucination rates, and conversational abilities. The experiments are conducted on different LLMs and IT datasets to ensure the findings are robust and generalizable. The authors use LoRA fine-tuning (LFT) and standard full-parameter fine-tuning (SFT). LFT works by approximating the model’s weight matrices with low-rank matrices, reducing the number of parameters that need to be fine-tuned. This makes the fine-tuning process faster. Contrary, SFT works by adjusting all or most of the model’s weights.

The main keypoints are:

- LoRA fine-tuning (LFT) preserves the pre-training token distribution while SFT doesn't. This means that using LFT, post fine-tuning the model still heavily relies on the pre-training and doesn't acquire new information.
    

![](https://media.licdn.com/dms/image/D4E12AQEWuBYI4ss3gQ/article-inline_image-shrink_400_744/0/1708898081111?e=1714608000&v=beta&t=uLpz3Sjn1cdk7AJ_gNCQQvrFTlLUlblk5TreulRL4Vw)

  

- Dataset scaling is ineffective for LFT
    

![](https://media.licdn.com/dms/image/D4E12AQHq9R_l0qxr2g/article-inline_image-shrink_400_744/0/1708898668150?e=1714608000&v=beta&t=jUqLYEdIZrsCI98KEoPB3hXayadl_1pg3F5UMcLoplc)

  

- LoRA fine-tuning mainly enhances response initiation and style without substantial knowledge enhancement.
    

![](https://media.licdn.com/dms/image/D4E12AQEfXLQbZIyYFQ/article-inline_image-shrink_400_744/0/1708898880173?e=1714608000&v=beta&t=ZpsrECAShZSWdZAYf_f4rYApwh-V92OEup3MFfJm7Bs)

  

- Full-parameter fine-tuning tends to degrade LLM knowledge base and increase hallucination occurrences.
    

![](https://media.licdn.com/dms/image/D4E12AQFLkW49INfVhQ/article-inline_image-shrink_1000_1488/0/1708899071346?e=1714608000&v=beta&t=vmv0to3yJBFO3sU0Bc1G0_uLYsRtoAjzEd-vInuaZfI)

  

- Popular methods and adjustments fail to significantly outperform simple LoRA fine-tuned models in terms of conversational quality and accuracy.
    

![](https://media.licdn.com/dms/image/D4E12AQGVw72EpQCHQA/article-inline_image-shrink_400_744/0/1708899193481?e=1714608000&v=beta&t=rJFe39mBGxJfzzed9HmRU4v8-Hx7MEA4HzexBYtbHFs)

  

## Conclusion

This paper shows that Instruction Tuning exhibits limitations in enhancing the conversational capabilities and knowledge base of LLMs. These limitations underscore the need for further research and development in this area. More details in the [full paper](https://huggingface.co/papers/2402.05119).

Congrats to the authors for their work!

Ghosh, Sreyan et al. “A Closer Look at the Limitations of Instruction Tuning.” _ArXiv_abs/2402.05119 (2024): n. pag.
