---
title:  "some LLM evaluation keywords explained"
image : "/assets/images/post/benchrobot.png"
author: "Ivan Gentile"
date: 2024-03-05 00:12:58 +0600
description: "few-shot, CoT, pass@1"
tags: [ LLM, evaluation, key-words, explained, benchmark]
---


When evaluating the capabilities of LLMs on tasks like question answering, researchers often use benchmarks consisting of carefully curated sets of questions (for an example check out [the "GPQA" benchamark](https://arxiv.org/abs/2311.12022) which I discovered recently... it just amazed me).

 The performance of the models on these benchmarks is then reported using various metrics and techniques. When you check out models system cards three important terms you'll frequently come across in this context are "x-shot," "CoT," and "pass@1."

### x-shots
The term "x-shot" refers to the number of examples or context provided to the LLM in the prompt before the actual question or task. For instance:

0-shot: No examples are provided, testing the model's ability to answer the question without any context.
5-shot: Five examples related to the task are provided as context before the question.
The more examples (or "shots") provided, the easier it becomes for the model to understand the task and potentially perform better. However, 0-shot evaluation is useful for assessing the model's general knowledge and reasoning abilities without relying on specific examples.

See [this medium article](https://medium.com/@mike_onslow/ai-simplified-exploring-the-basics-of-zero-shot-one-shot-and-few-shot-learning-d46248b5072a) for a quick visual understanding and 
[check out this paper for more](https://arxiv.org/abs/2109.01652).

### CoT
Chain of Thought (CoT) prompting is a technique that encourages the LLM to break down a problem into step-by-step reasoning before arriving at the final answer [check out the original Google Brain Meeting](https://arxiv.org/pdf/2201.11903.pdf). Instead of directly outputting the answer, the model is prompted to show its thought process, which can reveal valuable insights into its reasoning capabilities, 

Evaluations with CoT prompting typically score the model's full output, giving partial credit for correct steps, even if the final answer is wrong. This approach helps assess the model's ability to structure and reason through complex problems, rather than just its ability to produce the correct final answer.

![Chain of Thought from the Google Brain paper](/assets/images/post/cotapaper.png) 

### pass@1
"pass@1" refers to a type of evaluation where the model's output is taken as-is, and it is scored based solely on whether the final answer is correct or not. No partial credit is given for intermediate steps or reasoning.

Pass@1 evaluation is useful for tasks where the primary goal is to obtain the correct final answer, but it does not provide insight into the model's reasoning process. It is often used in conjunction with other evaluation methods, such as CoT prompting, to get a more comprehensive understanding of the model's capabilities.

### Recap

To recap and simplify:

Think of an LLM like a student.  "Shots"  are the examples you give the LLM to learn from.

- **Zero-shot**: You simply ask the LLM a question. It hasn't seen anything similar before.
- **One-shot**: You give the LLM one example of what you want it to do.
- **Few-shot**: You provide a handful of examples (usually 2-8).
The fewer shots an LLM needs to understand a task, the better it usually is.

**CoT** stands for "Chain of Thought." Here's how it improves LLMs:

- The Problem: LLMs sometimes gives you the wrong answer due to an unlucky sampling of tokens
- CoT Solution: With CoT prompting, you encourage the LLM to show its working step-by-step. This forces it to have a longer reasoning in terms of tokens before jumping to the answer, decreasing the chance of unlucky sampling. 

For **pass@1** we are checking if LLM's first answer attempt solve the task correctly.
A high pass@1 score means the LLM is accurate and nails the answer quickly.