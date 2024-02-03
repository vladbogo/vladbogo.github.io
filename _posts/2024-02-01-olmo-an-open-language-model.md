---
title: "OLMo - an Open Language Model"
categories:
  - Blog
---
OLMo is a new large language model introduced by the Allen Institute for Artificial Intelligence. It's achieves state of the art performance, surpassing LLaMA 2, and is truly Open Source. The authors have released the weights, training and inference code as well as the training data.

## The OLMo Framework

### Model architectures

OLMo comes in 3 size, a 1B and a 7B parameter that are already released and a 65B version that it's coming soon. Similar to other LLMs, it is using a decoder-only transformer architecture and it's trained on around 2T tokens. However it includes a series of changes over the vanilla transformer: no biases, non-parametric layer norm, SwiGLU activation function, Rotary positional embeddings and a vocabulary size of 50280.

![](https://media.licdn.com/dms/image/D4E12AQGzDCySHwgMrA/article-inline_image-shrink_400_744/0/1706826516475?e=1712188800&v=beta&t=CJbp0tsQGxrDiVCq2WPlLPfdsZse4TC5px5kW7NhXSM)

OLMo model sizes. The 65B version is currently still training

### Data

As part of the release, the authors include the dataset used for pre-training: Dolma. Dolma is a diverse, multi-source corpus of 3T tokens across 5B documents acquired from 7 different data sources as detailed below:

![](https://media.licdn.com/dms/image/D4E12AQGy3nAHlBLDaA/article-inline_image-shrink_400_744/0/1706826919075?e=1712188800&v=beta&t=JYcNqSduNxrLjwj5TUYbK_UJELf6K3mnoPaHZrK4P3s)

Dolma dataset details

### Evaluation

OLMo is evaluated on a series of downstream tasks and achieves state-of-the-art results when compared to other models, as detailed below:

![](https://media.licdn.com/dms/image/D4E12AQFPU9norej65Q/article-inline_image-shrink_400_744/0/1706827271681?e=1712188800&v=beta&t=NzbUlixNUIvWysV_unj_yf6UkBqYOoa1Rr1DFGIg10o)

OLMo-7B zero-shot evaluation

Moreover, it is also tested on intrinsic language modeling evaluation on a newly introduced perplexity benchmark called Paloma. Paloma includes 585 different text domains, ranging from [nytimes.com](http://nytimes.com/) to r/depression from Reddit.

![](https://media.licdn.com/dms/image/D4E12AQHGQLBjuijZCw/article-inline_image-shrink_400_744/0/1706827626292?e=1712188800&v=beta&t=b8rdZI0Y74t5vFp_qUA6Y71HWB1Rm33fJ5-V81IcXKA)

Paloma evaluation results

## Conclusion

OLMo introduces a new 7B model, with a larger 65B version planned for release soon. Unlike other models, OLMo's developers have shared the entire training and evaluation code, as well as the pre-training data. This approach not only supports further research but also enables a wide range of new applications! Kudos to the authors for their great work! For more details about OLMo, you can read the full paper [https://allenai.org/olmo/olmo-paper.pdf](https://allenai.org/olmo/olmo-paper.pdf).

**Other resources**:

Weights: [https://huggingface.co/allenai/OLMo-7B](https://huggingface.co/allenai/OLMo-7B)

Code: [https://github.com/allenai/OLMo](https://github.com/allenai/OLMo)

Data: [https://huggingface.co/datasets/allenai/dolma](https://huggingface.co/datasets/allenai/dolma)

Evaluation: [https://github.com/allenai/OLMo-Eval](https://github.com/allenai/OLMo-Eval)

Adaptation: [https://github.com/allenai/open-instruct](https://github.com/allenai/open-instruct)
