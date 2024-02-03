Understanding context is one of the key requirements for a Large Language Model. Although there's been a noticeable improvement in performance, with recent large language models (LLMs) demonstrating remarkable capabilities, there's a growing emphasis on evaluating their problem-solving quality rather than exploring their ability to comprehend context. This new study from Georgetown University and Apple introduces a new context understanding benchmark. The benchmark consist of four tasks and nine datasets:

![](https://media.licdn.com/dms/image/D4E12AQHrQpCfpUE5aA/article-inline_image-shrink_400_744/0/1706912262314?e=1712188800&v=beta&t=5Rn7js0CaozLxhiy3o8u1fhGqdzV_cUw6trEDY5rZ_E)

Tasks and datasets in the context understanding benchmark

## Coreference Resolution

The Coreference Resolution task involves identifying all expressions in a text that refer to the same entity. It directly contributes to achieving a coherent understanding of the overall message conveyed within the text. Two datasets were used in this benchmark: WSC273 and OntoNotes 5.0**.** Here's an example of what the model receives as input in order to measure the performance on the coreference resolution task:

![](https://media.licdn.com/dms/image/D4E12AQE5UDm-2CpAtQ/article-inline_image-shrink_400_744/0/1706904982664?e=1712188800&v=beta&t=4k1k6WpK5bmHR1pBbVEGeCbZNCNGJonXhV34QTjpBZI)

Coreference Example from OntoNotes 5.0 dataset

When it comes to the results, we can see that GPT-3.5-Turbo usually performs the best, but LLaMA 30B is not far behind. LLMs can usually handle _simple_ coreference relationships (WSC273 dataset), but they struggle on more complex documents (OntoNotes dataset). For all tasks, FT represents the results of finetuning on the task and acts as a reference point.

![](https://media.licdn.com/dms/image/D4E12AQEg4iCpIeRHQw/article-inline_image-shrink_400_744/0/1706912308726?e=1712188800&v=beta&t=1aesnCFx76gyaYoWwOH6IGEVOUjOviUuf84Ij8lK8wA)

Coreference Resolution Results

## Implicit Discourse Relation Classification

This task aims to assess the capabilities of identifying the different ways in which different segments of text are interconnected and to structure them in order to convey a coherent and meaningful message.

![](https://media.licdn.com/dms/image/D4E12AQFhc9sN219VBQ/article-inline_image-shrink_400_744/0/1706910871386?e=1712188800&v=beta&t=o3miFZJf7CMJEw-v5XWwzDIid2JF_iqC4na-zX7skFE)

Implicit Discourse Relation Classification Example

For this task, there seems to be a significant increase in score for models larger than 7B, but even for GPT-3.5-Turbo there is a significant gap as opposed to finetuning on this task:

![](https://media.licdn.com/dms/image/D4E12AQEgmF_Wljy-bw/article-inline_image-shrink_400_744/0/1706911086050?e=1712188800&v=beta&t=5HodYvmuEeo7aaR_URwum3EIQCOW8iCIwnxKfC1fEmY)

Implicit Discourse Relation Classification Results

## Dialogue State Tracking

The goal of Dialogue State Tracking is to track key information provided by the user as the conversation progresses. The dataset used for evaluating this task is MultiWOZ and you can see an example prompt below:

![](https://media.licdn.com/dms/image/D4E12AQFOKAGHTAZ5sw/article-inline_image-shrink_400_744/0/1706910407439?e=1712188800&v=beta&t=2QtuySxsjscTkd4jaz9ETFqjfltuqHhz49AS03CRGSQ)

Dialogue State Tracking example

The results follow the same trend as for Coreference Resolution where GPT-3.5-Turbo performs the best:

![](https://media.licdn.com/dms/image/D4E12AQF7Ueibpva4TA/article-inline_image-shrink_400_744/0/1706910721813?e=1712188800&v=beta&t=qs_EhmYootQU3wMhPi__hyvMv6M6J4LJ3xnOucNKQro)

Dialogue State Tracking results

## Query Rewriting

The Query Rewriting task is defined as rewriting the last utterance of a user in a conversation into an independent text that can be interpreted without any other context. The testing is conducted on five datasets.

![](https://media.licdn.com/dms/image/D4E12AQHm5-UGA3D9wQ/article-inline_image-shrink_400_744/0/1706905967165?e=1712188800&v=beta&t=u7X4Zm9JuK1F5rzTNCQ7UbzN-AjDwyWiO4MVQ9y9DJ8)

Query Rewriting example

For this task, there is a significant gap between small and large models, with smaller models performing a lot worse. Again GPT-3.5-Turbo performs the best.

![](https://media.licdn.com/dms/image/D4E12AQEM-DLNe_eamQ/article-inline_image-shrink_400_744/0/1706906151129?e=1712188800&v=beta&t=AWYlJFvFTAOl1lKNYhRXHsodcgZCcw__lYol6IPX6QA)

Query Rewriting results

## Conclusion

This paper introduces a contextual understanding benchmark designed to thoroughly assess the performance of LLMs. For more information please consult the full paper: [https://huggingface.co/papers/2402.00858](https://huggingface.co/papers/2402.00858). Kudos to the authors for their work!