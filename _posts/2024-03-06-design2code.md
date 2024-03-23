---
title: "Design2Code: How Far Are We From Automating Front-End Engineering?"
categories:
  - Blog
---
The paper proposes the Design2Code task and benchmark, which measures the ability of multimodal LLMs to automate front-end engineering by generating code implementations that directly render into the given reference webpages, given the screenshots as input.

## Method Overview

To measure the performance on the Design2Code task, the authors construct a manually curated benchmark of 484 diverse real-world webpages. They develop a set of automatic evaluation metrics that capture both high-level visual similarity (using CLIP embeddings) and low-level element matching (considering bounding box matches, text content, position, and color of matched visual elements).

The authors benchmark various multimodal large language models (LLMs), including GPT-4V and Gemini Pro Vision, using different multimodal prompting methods such as direct prompting (see prompt below), text-augmented prompting (providing extracted text elements), and self-revision prompting (asking the model to improve its previous generation). They also finetune an open-source 18B model, Design2Code-18B, on synthetically generated Design2Code data from the WebSight dataset.

![](https://media.licdn.com/dms/image/D4E12AQHt4vGDxZCs-A/article-inline_image-shrink_400_744/0/1709762425120?e=1716422400&v=beta&t=o250dZkpXr8U_ntm3HxK7MXBW9PFPvxuPIf6WKqBaRM)

For measuring performance, the authors use the following metrics:

High-Level Visual Similarity:

- CLIP Similarity: The similarity between the CLIP embeddings of the reference webpage screenshot and the generated webpage screenshot. This captures the overall visual similarity between the two images.

Low-Level Element Matching:

- Block-Match: Measures the total size of matched visual element blocks between the reference and generated webpages, relative to the total size of all blocks (matched and unmatched). This evaluates if all visual elements are reproduced correctly without missing or hallucinating elements.

- Text: The character-level similarity between the text content of matched blocks in the reference and generated webpages is calculated as twice the number of overlapping characters divided by the total number of characters in the two strings (character-level Sørensen-Dice similarity).

- Position: Computes the position similarity of matched blocks by comparing the normalized coordinates of their centers.

- Color: Uses the CIEDE2000 color difference formula to assess the perceptual difference between the colors of matched text blocks in the reference and generated webpages.


The authors intentionally do not combine these metrics into an aggregate score, as they are designed as fine-grained diagnostic scores, and models should ideally score well across all dimensions. The CLIP similarity captures high-level visual resemblance, while the element-matching metrics provide a detailed breakdown of performance on different aspects of webpage generation.

## Results

Both human evaluation and automatic metrics show that GPT-4V performs the best on this task compared to other models.


![](https://media.licdn.com/dms/image/D4E12AQEzOpcvLLmVXQ/article-inline_image-shrink_400_744/0/1709762424918?e=1716422400&v=beta&t=1lEOfZ3zaWiBfE_PojKLqpZBmn49lqy7UbGmOoTdAb8)
Human annotators find that in 49% of cases, GPT-4V generated webpages can replace the original reference webpages in terms of visual appearance and content. Surprisingly, in 64% of cases, GPT-4V generated webpages are considered better than the original reference webpages.

![](https://media.licdn.com/dms/image/D4E12AQH4iA_LLCgjxg/article-inline_image-shrink_1000_1488/0/1709762425004?e=1716422400&v=beta&t=0nBrBaLtUzBpfU-TbP2BayBVfu-fF1SVGehlr1Gp4Kc)
## Conclusion

The authors introduce the Design2Code benchmark and task, and conduct comprehensive benchmarking of multimodal LLMs on this task. For more information please consult the [full paper](https://huggingface.co/papers/2403.03163) or the [project page](https://salt-nlp.github.io/Design2Code/).

Dataset: [https://huggingface.co/datasets/SALT-NLP/Design2Code](https://huggingface.co/datasets/SALT-NLP/Design2Code)

Congrats to the authors for their work!

Si, C., et al. (2024). Design2Code: How Far Are We From Automating Front-End Engineering? arXiv preprint arXiv:2403.03163.
