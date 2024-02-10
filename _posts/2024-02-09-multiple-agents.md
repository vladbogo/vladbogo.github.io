---
title: "Harnessing the Power of Multiple Agents in Large Language Models"
categories:
  - Blog
---
A new paper titled "More Agents Is All You Need" from Tencent presents an approach to significantly enhance the performance of large language models (LLMs) through a simple yet effective method: use a sampling-and-voting mechanism to combine multiple agents and boost performance. Below you can see a teaser of the main results:

![](https://media.licdn.com/dms/image/D4E12AQGoFbTwR0Ge7Q/article-inline_image-shrink_400_744/0/1707516196826?e=1712793600&v=beta&t=BK3n9HxZRcXmBQowYAS_TWHRcZyhCVo_u72fsq1B7Xw)

The performance scales with the ensemble size

## Main idea

The core discovery of the study is that the performance of LLMs can be scaled effectively by simply increasing the number of instantiated agents and utilizing a sampling-and-voting method. In the **sampling phase**, the methods generates multiple responses from a LLM to a given query. This phase aims to cover a broad spectrum of possible answers by exploiting the model's capacity to produce varied outputs. Then, there is a **voting phase** where the model evaluates the generated responses and selects the most representative or accurate one through a majority voting mechanism. This could involve measuring similarity among responses or simply using the most frequent answer.

![](https://media.licdn.com/dms/image/D4E12AQHSQDTZlaP0wg/article-inline_image-shrink_400_744/0/1707516665850?e=1712793600&v=beta&t=_KLHO_-ZCKu7257EFzHjewaJhh4z6X5jb3aaZG_mfRM)

Method overview

This technique is orthogonal to existing methods, meaning it can work in conjunction with them to further enhance LLM performance.

## Results

Extensive experiments were conducted across a broad spectrum of LLM benchmarks to validate the findings. The method achieves significant performance gains across different tasks by scaling up the ensemble size. For instance, in arithmetic reasoning tasks, accuracy gains ranged from 12% to 24% on the GSM8K dataset and from 6% to 10% on the MATH dataset.

![](https://media.licdn.com/dms/image/D4E12AQEvAy5cn0863A/article-inline_image-shrink_400_744/0/1707517026978?e=1712793600&v=beta&t=E0kNCtLV2OFJI3N_dr3-9H7N_qgKEUrGfjyYoZhHv-M)

Consistent gains across tasks

The method not only generalizes across tasks but also demonstrates compatibility with other enhancement methods, paving the way for integrating this approach into a wide range of applications as shown below:

![](https://media.licdn.com/dms/image/D4E12AQE9h3O7PfbLPw/article-inline_image-shrink_400_744/0/1707517114363?e=1712793600&v=beta&t=CfzVzgaTQsd2VahyiyqMomZOTYL1i0v9nCDMjDrjTvw)

Combining multiple agents with other methods.

## Conclusion

This methods provides a simple, yet effective method to enhance the capabilities of LLMs without the need for complex alterations. By adding more agents the LLM performance can be significantly improved. For more information please consult the [full paper](https://huggingface.co/papers/2402.05120) and [code](https://anonymous.4open.science/r/more_agent_is_all_you_need/README.md).

Congrats to the authors for their great work!

Li, Junyou, Qin Zhang, Yangbin Yu, Qiang Fu and Deheng Ye. “More Agents Is All You Need.” (2024).
