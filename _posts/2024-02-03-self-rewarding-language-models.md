---
title: "Self-rewarding language models"
categories:
  - Blog
---
Learning from human feedback is crucial for developing effective Large Language Models. However, gathering such feedback on a large scale can be challenging. In this paper, the authors suggest that to create superhuman AI agents, we need feedback that goes beyond what humans can provide due to the sheer volume of data involved. To address this, they propose the use of self-reward mechanisms, where the model rewards itself during training through _LLM-as-a-Judge_ prompting.

## Self-rewarding

As in all LLM training, we want the model to have the ability to _follow_ _instructions_ and generate high quality responses. Additionally, for self-rewarding, the model needs to judge and generate new instruction-following examples.

Let's now see how we can train such a model!

### Training

The requirements for training include a pretrained large language model (M) and two datasets: one for instruction following fine-tuning and another containing examples of (prompt instruction, evaluated response) based on human feedback.

The iterative process can be outlined as follows:

1. Begin by fine-tuning model M conventionally.
    
2. Create new examples, asses and assign them a score using the model trained in the first step.
    
3. Incorporate the evaluated data into the training set and repeat the process.
    

![](https://media.licdn.com/dms/image/D4E12AQGXdoS4dT2rxw/article-inline_image-shrink_400_744/0/1707000045659?e=1712793600&v=beta&t=eE7XHlZxGZyz8KOHJ70eAMv180mK5KoX0oAJC3zf63o)

Self-Rewarding Language Models

To assess the quality of the newly generated data, the _LLM-as-a-Judge_ prompting technique is used. Essentially, the model is given through a new prompt, the instructions and the response it generated earlier, and it's asked to assess the quality of this new generation. Here's how this _LLM-as-Judge_ prompt looks like:

![](https://media.licdn.com/dms/image/D4E12AQGtjU_okgid8w/article-inline_image-shrink_1000_1488/0/1707001161680?e=1712793600&v=beta&t=kcQoMTdz0TXEhi3wB6JKP302GqOy4qJ95LkdAPRSFtk)

LLM-as-a-Judge prompting

## Results

For assessing the performance, the head-to-head win rate as judged by GPT-4 is used. More exactly, GPT-4 is presented with two choices and is asked to answer which is better. The results are quite impressive and the models obtained after each iteration are more and more powerful as seen below:

![](https://media.licdn.com/dms/image/D4E12AQEkUixofpi1PA/article-inline_image-shrink_400_744/0/1707001547424?e=1712793600&v=beta&t=vN9jpx1YEsnJOT5hx33rN140UJdG1PweqbCm28fZP_k)

Comparison between iterations

The authors also evaluate on the AlpacaEval 2.0 and the results are very interesting:

![](https://media.licdn.com/dms/image/D4E12AQGxOWqOL7synQ/article-inline_image-shrink_400_744/0/1707001614177?e=1712793600&v=beta&t=QeRgCxXf8vBJqNam6aO19Ea0grAuF-5ge-90Nt9HC7o)

AlpacaEval 2.0 Results

There is a huge increase in performance from a win rate of around 10% in the first iteration to 20% in the third one. This shows the potential of this proposed idea.

## Conclusion

The paper introduces Self-Rewarding Language Models capable of self-alignment through self-assessment and self-training on their generated outputs. The approach involves an iterative process where the model generates its own training data by assigning rewards to its own outputs using LLM-as-a-Judge prompting and then learning from these preferences. For more details please consult the full paper: [https://arxiv.org/pdf/2401.10020.pdf](https://arxiv.org/pdf/2401.10020.pdf).

Kudos to the authors for their great work!
