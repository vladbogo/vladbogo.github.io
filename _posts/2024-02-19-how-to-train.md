---
title: "How to Train Data-Efficient LLMs"
categories:
  - Blog
---
The evolution of large language models (LLMs) has reached a point where the balance between data consumption and model quality is one of the key challenges. With the increasing computational costs and diminishing returns from simply scaling up, the focus has shifted towards more data-efficient pre-training techniques. Today's paper aims to address these challenges by proposing a method of training data-efficient LLMs.

## Overview

The paper introduces two techniques: ASK-LLM and DENSITY. ASK-LLM leverages the zero-shot reasoning capabilities of instruction-tuned LLMs to directly assess the quality of a training example, while DENSITY aims to maximize coverage by modelling the data distribution to select a diverse set of samples.

Leveraging the reasoning capabilities of instruction-tuned LLMs, ASK-LLM addresses common shortcomings in traditional data quality assessment methods such as perplexity filters. It does so by evaluating training examples through a simple yet effective query: whether an example should be included in the training dataset as shown below:

![](https://media.licdn.com/dms/image/D4E12AQFh6nuGmxwX0Q/article-inline_image-shrink_1000_1488/0/1708380773895?e=1714003200&v=beta&t=6JyffYLDdh5YwRP0Ybaiq-5yPgcFtjNLpJGWsHSCyHw)

Ask-LLM prompt

The softmax probability of the response "yes," serves as the basis for the data quality score. This method effectively mitigates issues like lack of context, repetition of nonsensical content, and the unjust exclusion of informative niche topics.

The DENSITY sampler is designed to improve how well different topics are covered in the training data. It assumes that in any collection of data, some examples are common which have a lot of similar counterparts, while others are rare or unique. So, the goal of DENSITY is to boost the signal from under-represented portions of the input domain and downsample redundant, high-density information. It assumes access to a pre-trained embedding LLM and uses a sampling method based on kernel sums.

ASK-LLM and DENSITY are two different methods and can be used independently.

## Results

The methods are tested on 111 downstream tasks and the results are very promising. ASK-LLM enhances model performance efficiently, allowing for up to 90% of data rejection while achieving faster convergence (up to 70%)

![](https://media.licdn.com/dms/image/D4E12AQFBsa3qSWJnBg/article-inline_image-shrink_1000_1488/0/1708381577268?e=1714003200&v=beta&t=6kyGNW8Di7b3zNF3X5RIDB0e7-2bx0NF1uLyyImOb9g)

  

DENSITY prioritizes coverage over de-noising, maintaining the in-distribution test perplexity better than any other strategy (Figures 4a and 4d).

![](https://media.licdn.com/dms/image/D4E12AQFrWqW0uEQlPw/article-inline_image-shrink_400_744/0/1708381604563?e=1714003200&v=beta&t=8FbZb6iPvlPLUmGUaUHAEZliuBLbqQuCfYl6Pf-HsaY)

  

These findings highlight the effectiveness of intelligent data selection in optimizing model training processes.

## Conclusion

The effectiveness of ASK-LLM in quality filtering and DENSITY in maximizing coverage highlights the importance of intelligent data selection. These techniques offer a way for more resource-efficient LLM development which can have huge implications for future research. More details in the [full paper](https://huggingface.co/papers/2402.09668).

Congrats to the authors for their work!

Sachdeva, Noveen et al. “How to Train Data-Efficient LLMs.” (2024).
