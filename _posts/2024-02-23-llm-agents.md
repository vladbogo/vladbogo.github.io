---
title: "LLM Agents can Autonomously Hack Websites"
categories:
  - Blog
---
The paper explores the capability of Large Language Models (LLMs) to autonomously hack websites. It demonstrates that some models (especially GPT-4) can perform complex cybersecurity attacks, such as blind database schema extraction and SQL injections, without human intervention or prior knowledge of the vulnerabilities.

### Method Overview

The method creates an agent by using a LLM with function calling and extending some of its abilities: it gives the LLM access to a headless web browser, namely Playwright, which allows programatic access to websites. Additionally, the LLM is given 7 web hacking documents that are extracted and unmodified from online sources as part of its knowledge. Finally, through prompting, the LLM is given the ability to plan. The authors do not include the exact steps and prompts used intentionally and the goal of the paper is to raise awareness about the possibility of such attacks. Also, in order not to disrupt real-world systems, the authors perform these types of attacks on sandboxed websites and test for 15 vulnerabilities as detailed below:

![](https://media.licdn.com/dms/image/D4E12AQHJIHIPQ7Et2w/article-inline_image-shrink_1000_1488/0/1708726028452?e=1714003200&v=beta&t=DRQ3hC4LkXEfa-bX7T-DPoaS5itU8WZodNy-TpmTgFU)

  

### Results

The study found that GPT-4 successfully hacked 73.3% of the tested vulnerabilities, showcasing the significant offensive capabilities of LLMs. The results underline a scaling law where the success rate drops significantly with smaller models. For example, GPT-3.5 can only correctly execute a single SQL injection and fails on every other task, including simple and widely known attacks, like XSS and CSRF attacks. Also, all open-source models tested by the authors currently fail to perform these attacks.

![](https://media.licdn.com/dms/image/D4E12AQGI2W0ILGG6Gg/article-inline_image-shrink_400_744/0/1708726158803?e=1714003200&v=beta&t=IyRC-XAwytGwra2BgfOmn8COBRo-g9NJfQYIpSFenQM)

Hacking abilities of different agents

### Conclusion

The findings highlight the potential risks associated with the deployment of highly capable LLMs, as they can autonomously find and exploit web vulnerabilities. More details in the [paper](https://huggingface.co/papers/2402.06664).

Congrats to the authors for their work!

Fang, Richard et al. “LLM Agents can Autonomously Hack Websites.” _ArXiv_ abs/2402.06664 (2024): n. pag.
