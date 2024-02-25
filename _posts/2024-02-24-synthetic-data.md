---
title: Synthetic Data (Almost) from Scratch: Generalized Instruction Tuning for Language Models
categories:
  - Blog
---
Today's paper introduces Generalized Instruction Tuning (GLAN), a novel method for instruction tuning of Large Language Models (LLMs) using a pre-curated taxonomy of human knowledge and capabilities to generate synthetic instruction data across multiple disciplines. This method aims to improve LLMs' ability to follow human instructions without relying on specific task training data. The main idea is to address the limitations of current instruction tuning methods by proposing a scalable and general approach that leverages a systematic structure inspired by the human education system.

## Method Overview

GLAN constructs a taxonomy of human knowledge, breaks it down into disciplines, subjects, and key concepts, and then uses this structured information to generate diverse and comprehensive synthetic instruction data for tuning LLMs. Below you can find a comparison between GLAN and other methods from literature:

![](https://media.licdn.com/dms/image/D5612AQEZUeaG4QesZw/article-inline_image-shrink_1000_1488/0/1708811624756?e=1714003200&v=beta&t=wdpgtiN2Oqxl1DBwBTmJGvDKO3zH3VV_vbRQEV_braM)

  

GLAN utilizes LLMs like GPT-4 to create a comprehensive taxonomy of human knowledge, organizing it into _fields_, _sub-fields_, and _disciplines_. This taxonomy guides the autonomous generation of subjects for each discipline, then a syllabus for each subject, outlining key concepts and class sessions. Then, GPT-4 is prompted to generate homework questions based on these elements. This methodical breakdown from broad disciplines to atomic-level components like class sessions and key concepts helps generating a comprehensive set of synthetic instruction data that is used for training/fine-tuning of other models. The process is formalized below:

![](https://media.licdn.com/dms/image/D5612AQGFTAnublmp-w/article-inline_image-shrink_400_744/0/1708812466636?e=1714003200&v=beta&t=Zw5ZhSP1yEwQ5qFLyrDAdCyrFmriTHM90pNiftZdS7I)

  

## Results

Extensive experiments demonstrate that GLAN significantly enhances the base LLMs' performance across various tasks, including mathematical reasoning, coding, logical reasoning, and general instruction following, without using task-specific training data. In the experiments, the authors use a Mistral-7B model. Here are the results:

![](https://media.licdn.com/dms/image/D5612AQF2nQ4UBRvELA/article-inline_image-shrink_400_744/0/1708812761465?e=1714003200&v=beta&t=gmyyIP9ksNL1EBKYGg9gmD3sYepGsSnKVlTCPUv_ouA)

  

## Conclusion

GLAN proposes an interesting way to generate synthetic instruction tuning data for LLMs, showing promising results on multiple tasks. For more informations, please consult the [full paper](https://huggingface.co/papers/2402.13064).

Congrats to the authors for their work!

Li, Haoran et al. “Synthetic Data (Almost) from Scratch: Generalized Instruction Tuning for Language Models.” (2024).
