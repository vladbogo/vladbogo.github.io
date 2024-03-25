---
title: "VideoMamba: State Space Model for Efficient Video Understanding"
categories:
  - Blog
---
The paper proposes VideoMamba, a state space model (SSM)-based approach for efficient video understanding. It aims to address the challenges of local redundancy and global dependencies in video data, leveraging the linear complexity of the Mamba operator for long-term modeling.

## Method Overview

VideoMamba extends the bidirectional Mamba block, originally designed for 2D image processing, to handle 3D video sequences. It follows the architecture of vanilla Vision Transformers (ViT), with a 3D patch embedding layer that divides the input video into non-overlapping spatiotemporal patches. These patches are then flattened and mapped to a sequence of tokens, which are processed by stacked B-Mamba blocks.


![](https://media.licdn.com/dms/image/D4E12AQE9hh1Yehy2YQ/article-inline_image-shrink_1000_1488/0/1710629443319?e=1715817600&v=beta&t=OUVmSQefWORqmmo30hX_KTgRn3yGmnFxG3Tjh3xlMF0)

  
The authors explore different spatiotemporal scan orders for the B-Mamba blocks, including spatial-first, temporal-first, and hybrid scans. Through experiments, they find the spatial-first bidirectional scan to be the most effective, as it can seamlessly leverage 2D pretrained knowledge by scanning frame by frame.

To enhance the scalability of larger VideoMamba models, the authors introduce a self-distillation technique. A smaller, well-trained model acts as a "teacher" to guide the training of a larger "student" model by aligning their final feature maps, mitigating overfitting issues observed in larger Mamba architectures.

![](https://media.licdn.com/dms/image/D4E12AQGmBnMJOdKdiA/article-inline_image-shrink_400_744/0/1710629443153?e=1715817600&v=beta&t=SjFILweM0FhUJjxigkxBYmlqXPqfcnM3wYsEOdbApnI)

Additionally, VideoMamba adapts masked modeling techniques to improve its temporal sensitivity and multi-modal compatibility. The authors propose row masking strategies tailored to the 1D convolution within B-Mamba blocks, exploring random, tube, clip-row, frame-row, and attention-based masking. They also investigate aligning only the final outputs between the student and teacher models due to architectural differences.

![](https://media.licdn.com/dms/image/D4E12AQEC9jgDdQQ0Zg/article-inline_image-shrink_400_744/0/1710629443412?e=1715817600&v=beta&t=_zsBK6AABGOqNP5aThgsl8_hLrBwPCfqVCnBTW-uVYQ)

## Results

- Scalability: VideoMamba outperforms other isotropic architectures on ImageNet-1K, achieving 84.0% top-1 accuracy with only 74M parameters.

![](https://media.licdn.com/dms/image/D4E12AQFnjoxZWlZczw/article-inline_image-shrink_1000_1488/0/1710629491885?e=1715817600&v=beta&t=TLyYR-VJYchNvEfcV0RiijXA4HzEXE1-foNlBr2haYk)

- Short-term Action Recognition: On Kinetics-400 and Something-Something V2, VideoMamba surpasses attention-based models like ViViT and TimeSformer, with reduced computational demands.

![](https://media.licdn.com/dms/image/D4E12AQHiA2RgsAXN9A/article-inline_image-shrink_1000_1488/0/1710629521095?e=1715817600&v=beta&t=uVVizdxPDbGc4SZ5JtkbtRmC5SAzy-2mFQwVkMIqgC4)


- Long-term Video Understanding: VideoMamba demonstrates remarkable superiority over traditional feature-based methods on the Breakfast, COIN, and LVU benchmarks, setting new state-of-the-art results.

- Multi-modality: VideoMamba achieves improved performance in zero-shot video-text retrieval tasks, showcasing its robustness in multi-modal contexts.

![](https://media.licdn.com/dms/image/D4E12AQF6Y35hLimsyA/article-inline_image-shrink_1000_1488/0/1710629541722?e=1715817600&v=beta&t=8E1Xeul59M5Y4Krdkl-uJ10DmjJrOCpBVxfI6bc0dNo)

## Conclusion

VideoMamba adapts the Mamba architecture for efficient long-term video modeling, outperforming existing methods in various video understanding tasks. For more details please consult the [full paper](https://huggingface.co/papers/2403.06977) or the [code](https://github.com/OpenGVLab/VideoMamba).

Congrats to the authors for their work!

Model: [https://huggingface.co/OpenGVLab/VideoMamba](https://huggingface.co/OpenGVLab/VideoMamba)

Li, Kunchang, et al. "VideoMamba: State Space Model for Efficient Video Understanding." arXiv preprint arXiv:2403.06977, 2023.
