---
title: "Recovering the Pre-Fine-Tuning Weights of Generative Models"
categories:
  - Blog
---
Spectral DeTuning is a new method that successfully recovers the original weights of generative models before they were fine-tuned with human feedback or other customization. It shows that pre-fine-tuning weights are recoverable and methods fine-tuned with LoRA can be susceptible to a new weight recovery type of attack.

## Method overview

The paper first introduces the task of _Pre-Fine-Tuning Weight Recovery_. The goal is to recover the weights before fine-tuning given a model. In the paper, the assumption is that the model fine-tuning was performed using LoRA. Here's an overview of the task:

![](https://media.licdn.com/dms/image/D4E12AQGAb8prZOX8Ig/article-inline_image-shrink_400_744/0/1708343885870?e=1714003200&v=beta&t=WohNOTlaqsDdB1mk999q_8oqZHznynsUM82uTgw3M2I)

Pre-Fine-Tuning Weight Recovery Setting - The attacker, with access to multiple Low-rank Adaptation (LoRA) fine-tuned models but without the models' detailed low-rank decomposition, tries to reconstruct the original weights.

The Spectral DeTuning method uses the assumption that fine-tuning generative models often involves adjusting a relatively small set of parameters, leaving the underlying structure largely intact. By exploiting this characteristic, the method applies a spectral analysis technique to identify and reverse these minor adjustments, effectively rolling back the model to its pre-fine-tuned state. To recover Pre-FT (pre-fine-tuned) weights, the process involves predicting the original weight matrix (WP) from n fine-tuned weight matrices. This is done by utilizing differences in up to r principal components from these matrices and framing it as an optimization problem. Each LoRA (Low-rank Adaptation) fine-tuned model adds constraints to WP.

The authors also create a dataset (_LoWRA Bench_) that tackles this task. The dataset includes three main pre-trained source models: a Vision Transformer (ViT) for images, Mistral-7B-v0.1, and Stable Diffusion 1.5, covering both vision and language processing tasks. It features 15 LoRA fine-tuned models per source model across various datasets and objectives, totaling 544 source model layers and over 8,000 layers when including fine-tuned layers. This diverse set allows for extensive testing of methods to recover pre-fine-tuned model states, assessing their effectiveness across different model types, layer types, and depths.

## Results

The results are reported for different base models such as Stable Diffusion and Mistral. The results show that personalization methods that use LoRA are vulnerable to Pre-Fine-Tuning Weight Recovery attacks. The metrics depend from model to model. For Stable Diffusion, it uses LPIPS distance between the generated image by the Pre-Fine-tuned model and the recovered model, while for Mistral it's the log cosine distance between the Sentence-BERT embeddings of the generated text for the Pre-Fine-tuned model and the recovered one.

![](https://media.licdn.com/dms/image/D4E12AQHeGQ3sNIOx3w/article-inline_image-shrink_1500_2232/0/1708343797443?e=1714003200&v=beta&t=yx-JsYAS_9zfULtmdkJyKa-grGayaf9RnWm82fiSfgE)

Stable Diffusion results

![](https://media.licdn.com/dms/image/D4E12AQGz0se8D8mvNA/article-inline_image-shrink_1500_2232/0/1708343830090?e=1714003200&v=beta&t=sQIlyinmRP7u2WWEN6PoiPQpepRkdMgSTKNFFXFfTNQ)

Mistral results

![](https://media.licdn.com/dms/image/D4E12AQHR7lTUOG0QRg/article-inline_image-shrink_1500_2232/0/1708343844625?e=1714003200&v=beta&t=3QiTDUV2TJuqmuwETeKIYGWxh2WXXGXnVVtANen_-Fs)

Qualitative results for Stable Diffusion

## Conclusion

The paper introduces Spectral DeTuning, a method to accurately and efficiently recover the exact pre-fine-tuning weights. It also raises important considerations for the security and integrity of fine-tuned models, as it reveals that seemingly irreversible changes can indeed be undone. For more details please consult the [full paper](https://huggingface.co/papers/2402.10208).

### Other resources

Code: [https://github.com/eliahuhorwitz/Spectral-DeTuning](https://github.com/eliahuhorwitz/Spectral-DeTuning)

Project page: [https://vision.huji.ac.il/spectral_detuning/](https://vision.huji.ac.il/spectral_detuning/)

Dataset LoWRA: [https://huggingface.co/datasets/Eliahu/LoWRA-Bench](https://huggingface.co/datasets/Eliahu/LoWRA-Bench)

Congrats to the authors for their work!

Horwitz, Eliahu et al. “Recovering the Pre-Fine-Tuning Weights of Generative Models.” (2024).
