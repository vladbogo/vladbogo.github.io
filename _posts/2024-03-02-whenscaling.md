---
title: "WHEN SCALING MEETS LLM FINETUNING: THE EFFECT OF DATA, MODEL AND FINETUNING METHOD"
categories:
  - Blog
---
This paper provides a systematic study on how different scaling factors affect the performance of large language model (LLM) finetuning. Specifically, it explores the impact of factors like LLM model size, pretraining data size, finetuning data size, and tunable parameter sizes for parameter efficient tuning (PET) methods such as prompt tuning and LoRA.

## Downstream Tasks

In order to be able to assess the impact of various factors for fine-tuning, the authors choose the machine translation and multilingual summarization as downstream tasks. More exactly, they pre-train multiple English-German and English-Chinese bilingual LLMs with sizes ranging from 1B to 16B parameters on around 280B tokens as described below:

Minimize image

Edit image

Delete image

![](https://media.licdn.com/dms/image/D4E12AQHPamlmbG3I_g/article-inline_image-shrink_400_744/0/1709399920123?e=1716422400&v=beta&t=jDcEbZXq0mjRi2Zdia3Kt3bapRfIETw9WNUP-OtCNGU)

  

These models are then finetuned on downstream tasks of machine translation and multilingual summarization using full-model tuning (FMT) that updates all parameters or parameter efficient methods (PET) like such as Prompt Tuning or LoRA. The finetuning data regime varies from thousands to millions of examples. A novel multiplicative joint scaling law is proposed to characterize the interaction between finetuning data size and factors like LLM size. Extensive experiments are performed to derive empirical scaling trends.

## Results

Now let's look at some key results:

- "LLM finetuning benefits more from LLM model scaling than pretraining data scaling across tasks and methods**"**
    

Minimize image

Edit image

Delete image

![](https://media.licdn.com/dms/image/D4E12AQGv5kt1xECEZQ/article-inline_image-shrink_400_744/0/1709400157012?e=1716422400&v=beta&t=BsaSYSg6VID8QqwhCGhe84eV3JdMB466bNZM_NoWJYs)

  

  

- "Scaling PET parameters is ineffective, delivering limited gains for both LoRA and Prompt"
    

Minimize image

Edit image

Delete image

![](https://media.licdn.com/dms/image/D4E12AQHxWSJYpte_Fw/article-inline_image-shrink_1000_1488/0/1709400171789?e=1716422400&v=beta&t=QH2YZI9OAXDSVYDsnCDEnW3xwcYQ4AFBBUr_YYyUH20)

  

- "Finetuning data have more pronounced influence on FMT than PET, where LoRA scales better than Prompt"
    

Minimize image

Edit image

Delete image

![](https://media.licdn.com/dms/image/D4E12AQFHQ0TOxpT1TA/article-inline_image-shrink_1000_1488/0/1709400191399?e=1716422400&v=beta&t=PQfL071k6cvbFP4gWjWQ-JM4dnphoeqZjsQ8QfFXdxY)

  

- "PET depends more on LLM model and pretraining data scaling than finetuning data scaling across settings"
    

  

## Conclusion

In this paper, the authors study the scaling for LLM finetuning, considering different factors such as LLM model size, pretraining data size, finetuning data size, PET parameter size. The results show that increasing LLM model size has a higher impact on finetuning than pretraining data scaling. Also, scaling PET parameter is ineffective. More details in the [full paper](https://huggingface.co/papers/2402.17193).

Congrats to the authors for their work!

Zhang, Biao et al. “When Scaling Meets LLM Finetuning: The Effect of Data, Model and Finetuning Method.” (2024).
