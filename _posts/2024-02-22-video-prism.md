---
title: "VideoPrism: A Foundational Visual Encoder for Video Understanding"
categories:
  - Blog
---
VideoPrism is a a versatile video encoder that enhances video understanding across various tasks with a single model. It uses a large dataset of over 36 million high-quality video-caption pairs and 582 million video clips with noisy associated texts (extracted from ASR - Automatic Speech Recognition) for training. During pretraining, it uses global-local distillation of semantic video embeddings and a token shuffling scheme, allowing the model to focus on the video modality while leveraging the text. VideoPrism achieves state-of-the-art performance on a wide range of video understanding benchmarks (30 out of 33 tested benchmarks).

## Method Overview

VideoPrism uses a two-stage training process. Initially, the model uses a video-text to align the video encoder with the text encoder using all the video-text pairs. To achieve this, it minimizes a symmetric cross-entropy loss over the similarity scores of all video- text pairs. Then, in stage two, the process continues using an improved masked autoencoding on video clips only.

![](https://media.licdn.com/dms/image/D4E12AQEX5AB17_jKlA/article-inline_image-shrink_400_744/0/1708628541956?e=1714003200&v=beta&t=UEeCev4J00qEUMmu3WlTCj64saUXk5bSAPaLpaIGpxA)

VideoPrism training stages

The authors argue that it is challenging to train solely on vision-text data as in the first stage. This happens because text descriptions can be noisy, and they often capture appearance more than motion. So, in order to address this, the process shifts towards learning both appearance and motion from video-only data using a masked autoencoding approach, but with some improvements: a new t_oken shuffling_ scheme to prevent decoding shortcuts and _global and token-wise distillation_ to effectively leverage the knowledge acquired in the first stage. More exactly, the second-stage (student) model learns to predict the first-stage (teacher) model’s embeddings of _all_ tokens based on a masked video.

## Results

VideoPrism has been extensively tested across four broad categories of video understanding tasks: (1) general video-only understanding, (2) zero-shot video-text retrieval, (3) zero-shot video captioning and QA and (4) CV for science. It achieves state-of-the-art results on 30 out of 33 benchmarks. This demonstrates its capability to generalize across a diverse set of video understanding challenges.

![](https://media.licdn.com/dms/image/D4E12AQEp9Nc8B4TiyA/article-inline_image-shrink_400_744/0/1708629344670?e=1714003200&v=beta&t=JOoZV-VrzGIqeNZFGOoto8Qr1AF_HaqFypZwP5pB52k)

  

![](https://media.licdn.com/dms/image/D4E12AQFwMFfQLpOCMw/article-inline_image-shrink_400_744/0/1708629366950?e=1714003200&v=beta&t=y8tvx3IrkObuMm1qZ--wQWkgA0uXjqHmKIP6MzM_lJQ)

  

## Conclusion

VideoPrism achieves state-of-the-art performance across a wide range of video understanding tasks by leveraging a comprehensive pretraining strategy in order to learn both appearance and motion. More details in the [full paper](https://huggingface.co/papers/2402.13217).

Congrats to the authors for their work!

Zhao, Long et al. “VideoPrism: A Foundational Visual Encoder for Video Understanding.” (2024).
