---
title:  "Una Pipeline per migliorare gli LLM in Italiano"
image : "/assets/images/post/italianrobt.png"
author: "Ivan Gentile"
date: 2024-01-25 17:12:58 +0600
description: "Dalla preparazione di un dataset di domande e risposte"
tags: [AI, LLM, OpenAI, Mistral, Neural Networks, Fine-tuning, Machine Learning Pipeline, Data Prepartion, Deep Learning]
---



## Introduzione

Siamo tutti consapevoli delle potenzialità di ChatGPT. Si tratta probabilmente della killer app della decade (forse del secolo se i progressi continuano allo stesso rate?) e da quando è uscita ha completamente stravolto il mio modo di lavorare, imparare e quasi sicuramente di pensare. 

Un problema al momento non ancora molto pronunciato ma che vedo crescere molto in fretta (a meno di un incredibile successo di progetti come  [Modello Italia](https://it.igenius.ai/blog/igenius-and-cineca-announce-modello-italia)) è la differenza in performance di un modello SOTA in Inglese rispetto che in Italiano. 

Se così, vedremo aumentare quelli che sono oggi gli svantaggi tra una persona che non è fluente in Inglese.
Non solo faticherà a sfruttare la vastità di risorse in Inglese sul web, ma non potrà sfruttare al massimo i futuri GPT che da queste risorse *avranno estratto ancora più conoscenza*. 

Per metterci una pezza, il finetuning di **Foundation Models** per migliorare le loro capacità in Italiano sembra una strategia valida.
 
Per arrivare al finetuning dobbiamo passare prima però per altri step molto importanti. 

## Data Preparation

Lasciando da parte per il momento la prepazione dell'ambiente di sviluppo sul quale condurre il finetuning, come in qualsiasi progetto di machine learning è ottima pratica partire dai dati. 

Recentemente molti articoli scientifici hanno dimostrato come [la qualità dei dati sia fondamentale](https://arxiv.org/abs/2306.11644)(forse [ancora più della quantità](https://arxiv.org/abs/2308.12032) ) per la riuscita di un finetuning di qualità. Niente di nuovo sotto il sole: 
- Garbage in, Garbage out. 
- Ma è bello sapere **Gold in, Gold out** per quanto riguarda il finetuning di [*downstream task*](https://www.baeldung.com/cs/downstream-tasks) di un LLM.

L'ambizione qui è di riuscire a creare un dataset di alta qualità di *coppie istruzioni-risposte* adottando un alto livello di automazione. L'ispirazione è seguire metodologie introdotte in [ORCA](https://arxiv.org/abs/2306.02707) e [WizardLM](https://arxiv.org/abs/2304.12244) ed ottenere un qualcosa simile all'[alpaca dataset](https://github.com/tatsu-lab/stanford_alpaca/blob/main/alpaca_data.json). (Ma noi abbiamo letto da poco quest'altro bell'[articolo](https://arxiv.org/abs/2401.08500) e proveremo ad ottenere il dataset in yaml invece che json)

Ci saranno anche delle sfide di [formattazione](https://huggingface.co/blog/chat-templates) ed [altro](https://colab.research.google.com/drive/1GH8PW9-zAe4cXEZyOIE-T9uHXblIldAg?usp=sharing), ma le affronteremo più avanti.

## Il Fine-Tuning Vero e Proprio
Un'altra serie di scelte che dovremo affrontare: 

1. **Scelta del modello**: Bisognerà optare per un modello pre-addestrato con licenza pubblica che si adatti bene al nostro task, ovvero che sappia già essere un bravo interlocutore in Inglese e possa diventarlo in Italiano. Pensate anche voi già a LLaMA2 (come i [LLaMAntini](https://arxiv.org/abs/2312.09993))? Oppure siete curiosi di vedere [MixTral](https://mistral.ai/news/mixtral-of-experts/) in azione? 
   
2. **Scelta del Tokenizer**: Tutta un'altra [storia](https://huggingface.co/docs/transformers/main_classes/tokenizer)

3. **Scelta di Iperparametri**: Sarà a tutti gli effetti un esperimento di machine learning! 

4. **Efficientamento**: [LoRA](https://arxiv.org/abs/2106.09685), [QLoRA](https://arxiv.org/abs/2305.14314), [Flash Attention](https://arxiv.org/abs/2205.14135)... vediamo come ci arriviamo prima

5. **Testare e Valutare il Modello dopo il FineTuning**

## Aperture

Bene direi che più o meno l'idea in testa ce l'abbiamo, e i primi step sono chiari... possiamo iniziare!

