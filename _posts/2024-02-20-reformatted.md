---
title: "Reformatted Alignment"
categories:
  - Blog
---
The paper introduces REALIGN, a novel approach aimed at enhancing the quality of instruction data for large language models (LLMs) to better align with human values. This method _reformats_ instruction data responses into a format that aligns with pre-established criteria and evidence, reducing errors and scaling issues associated with manual annotation and LLM hallucinations. The method is orthogonal to existing techniques and shows significant improvements in LLM performance without requiring new data or advanced training techniques.

## Method Overview

REALIGN operates in three main steps: **criteria definition**, where preferences for various scenarios are defined; **retrieval augmentation**, which broadens the knowledge base for tasks; and **reformatting**, which aligns responses with criteria and evidence. Here's the overview:

![](https://media.licdn.com/dms/image/D4E12AQE8-ebqgqcWbg/article-inline_image-shrink_400_744/0/1708467309468?e=1714003200&v=beta&t=LUS1QUYIJnweJmOUX6fyEW-faEAofW3z05jpz694Ifs)

REALIGN overview

So, given a dataset of pairs (query, response), REALIGN reformats the response and changes the dataset. This dataset is now used for fine-tuning as opposed to the original dataset. Here's a qualitative example on how the response looks like before and after applying REALIGN:

![](https://media.licdn.com/dms/image/D4E12AQFVcOKJgP6sxg/article-inline_image-shrink_1000_1488/0/1708467920869?e=1714003200&v=beta&t=loBWguENdurO2SYQ4cv-wpSH3jOgb-38nyRby0Te5eo)

Original response (left) vs REALIGN response (right)

## Results

Experiments show that REALIGN significantly improves LLMs in terms of general alignment, math reasoning, factuality, and readability. For instance, it increased the math reasoning ability of LLaMA-2-13B from 46.77% to 56.63% in accuracy.

![](https://media.licdn.com/dms/image/D4E12AQH6izwulv5Jmw/article-inline_image-shrink_1000_1488/0/1708467985540?e=1714003200&v=beta&t=gehUGJRn5p0R8VAl-LF5kRiOfOwHB4JXoX5d0zH1UGQ)

Math reasoning results

Moreover, 5% of REALIGN data resulted in a 67% boost in general alignment ability, indicating the method's efficiency and effectiveness. These results highlight the potential of REALIGN to enhance the performance of LLMs across various tasks without additional data or complex training methodologies.

![](https://media.licdn.com/dms/image/D4E12AQEl7yO3HS8AnA/article-inline_image-shrink_1000_1488/0/1708468078522?e=1714003200&v=beta&t=B5TfX2BhoQ_OYdxyFcQom3AwA0rHHFkWrlLpT07_9a0)

  

### Conclusion

REALIGN presents a simple and efficient method for improving the alignment of LLMs with human values through reformatting the instruction data. For more details please consult the [full paper](https://huggingface.co/papers/2402.12219) and the [code](https://github.com/GAIR-NLP/ReAlign).

Congrats to the authors for their great work!

Fan, Run-Ze et al. “Reformatted Alignment.” (2024).
