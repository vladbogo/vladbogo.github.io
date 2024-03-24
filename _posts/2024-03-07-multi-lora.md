---
title: "Multi-LoRA Composition for Image Generation"
categories:
  - Blog
---
The paper introduces two new methods, LoRA Switch and LoRA Composite, for composing multiple Low-Rank Adaptations (LoRAs) for the task of text-to-image generation. The main idea is to explore a decoding-centric perspective, where the LoRA weights are kept intact, and the composition is achieved by selectively activating LoRAs during the denoising process of diffusion models. The paper also proposes ComposLoRA a testbed consisting of 480 composition sets used to measure the performance.

## Method Overview

The authors introduce two new methods of composing LoRAs: LoRA Switch and LoRA composite.

![](https://media.licdn.com/dms/image/D5612AQH-h9dv9ZCOeA/article-inline_image-shrink_1000_1488/0/1709854314823?e=1716422400&v=beta&t=KqC27BpVuLTWBFIdrhLAMxrzE2ra2n20P15ddkrWwGI)

1. LoRA Switch (LoRA-S): This method activates a single LoRA at each denoising step, cycling through different LoRAs in a predetermined sequence and changing the active LoRA after each _t_ steps. In this way, each LoRA contributes repeatedly to the image generation with the goal of achieving a better generation.

2. LoRA Composite (LoRA-C): This method involves calculating unconditional and conditional score estimates for each LoRA individually at every denoising step. These scores are then averaged to provide balanced guidance throughout the image generation process, ensuring the cohesive integration of all elements represented by different LoRAs.

In order to test the results, the paper introduces ComposLoRA, a comprehensive testbed featuring several LoRAs and 480 composition sets, to evaluate the proposed methods. More exactly, from a collection of public LoRAs, the authors select 22 of them that are combined together in order to form the compositions. For evaluation, the authors propose a GPT-4V based framework, where GPT-4V assesses the image quality and the composition quality of the generated images.

![](https://media.licdn.com/dms/image/D5612AQGQdxGMF0IlLw/article-inline_image-shrink_400_744/0/1709854315054?e=1716422400&v=beta&t=MfiXQC_oCXUpxbewwNhadYRhRQ-zEowOrk_jbgXpNlc)
## Results

- Extensive automatic and human evaluations demonstrate the superior performance of LoRA Switch and LoRA Composite compared to the prevalent LoRA merging approach, especially as the number of LoRAs in a composition increases.

![](https://media.licdn.com/dms/image/D5612AQHgjRMEcSspfQ/article-inline_image-shrink_1000_1488/0/1709854314886?e=1716422400&v=beta&t=BQSaWUan65bEg3HtE8xetrpK3FPtGOBvCLetuIZpohk)

![](https://media.licdn.com/dms/image/D5612AQFLn277iea47A/article-inline_image-shrink_400_744/0/1709854314861?e=1716422400&v=beta&t=0jeTHcNZw5npJtZALSI7yQ1iozCeJuqYgFnm607Yaj8)

- LoRA Switch excels in composition quality, while LoRA Composite performs better in image quality.

![](https://media.licdn.com/dms/image/D5612AQFFTZhOV6tD1w/article-inline_image-shrink_1000_1488/0/1709854485384?e=1716422400&v=beta&t=5dGbJg8UiJ52LmuyenFBsfZLJnnz94wlkTH8iopDDFg)

![](https://media.licdn.com/dms/image/D5612AQFaO6CWCuttOA/article-inline_image-shrink_1000_1488/0/1709854522235?e=1716422400&v=beta&t=GF6szMU6e1c_DS6m53zY7VUnTGhRhGAkS8EHiHE9kVI)

## Conclusion

The paper introduces two training-free methods, LoRA Switch and LoRA Composite. These methods overcome the limitations of current weight manipulation techniques and enable the effective integration of multiple LoRAs for composable image generation. For more details please consult the [full paper](https://huggingface.co/papers/2402.16843) and the [project page](https://maszhongming.github.io/Multi-LoRA-Composition).

Congrats to the authors for their work!

Zhong, Ming, et al. "Multi-LoRA Composition for Image Generation." ArXiv, 26 Feb. 2024, arxiv.org/abs/2402.16843.
