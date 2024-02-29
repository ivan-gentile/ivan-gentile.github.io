---
title:  "RAG vs FineTuning"
image : "/assets/images/post/nerdy_robot_with_books_in_t_6163e123-afce-47f8-b003-1e8ccc62eb49.png"
author: "Ivan Gentile"
date: 2024-02-29 00:12:58 +0600
description: "Introduzione e risorse"
tags: [AI, LLM, OpenAI, Mistral, Neural Networks, Fine-tuning, Machine Learning Pipeline, Data Prepartion, Deep Learning]
---



Per migliorare le capacità degli LLM preaddestrati è possibile seguire due strategie: 
1. Un approccio basato su Retrieval-Augmented Generation (RAG)
2. Un fine-tuning del modello preaddestrato

### RAG
L'approccio **RAG** mira a potenziare le capacità dell'LLM attraverso l'integrazione di un sistema di retrieval. Questo sistema estrae frammenti di documenti pertinenti da un ampio corpus informativo, fornendo al modello una base di conoscenza esterna da consultare per generare risposte più accurate e dettagliate [link al paper](https://arxiv.org/abs/2005.11401). In pratica, RAG permette al modello di accedere e utilizzare informazioni aggiuntive durante il processo di generazione del testo, migliorando significativamente la qualità delle sue risposte.

Si distinguono diverse metodi di implementazione della tecnologia RAG. In particolare RAG opera utilizzando una sequenza di input per recuperare documenti di testo, che vengono poi utilizzati come contesto aggiuntivo per generare la sequenza di output e si possono impiegare due approcci per la generazione del testo: RAG-Sequence e RAG-Token. Mentre il modello RAG-Sequence utilizza lo stesso documento per tutta la generazione della sequenza, il modello RAG-Token può utilizzare documenti diversi per ogni token, offrendo flessibilità nella generazione di risposte da molteplici fonti. Alcuni riferimenti che propongono spiegazioni semplici di tali processi sono disponibili in una [video serie di Donato Capitella](https://www.youtube.com/watch?v=7yXVhDz3OD8)

Essenziale all'interno di questo contesto è il concetto di vector retrieval, che viene ampiamento esplorato in questo [libro sul vector retrieval](https://arxiv.org/abs/2401.09350).

### Finetuning 
La strategia di **fine-tuning**, d'altra parte, consiste nell'adattare un LLM preaddestrato a un compito specifico mediante un ulteriore addestramento su un set di dati più piccolo e focalizzato. Questo metodo affina le capacità del modello per migliorare le prestazioni in compiti specifici, rendendolo più efficace nell'interpretare le richieste dell'utente e nel fornire informazioni pertinenti nel contesto di una webapp.

Un esempio avanzato di tale approccio è illustrato in questo [oaper su Reinforcement Learning with Human Feedback](https://arxiv.org/abs/2305.18438). Questo studio si concentra sull'apprendimento per rinforzo offline con feedback umano (RLHF), con l'obiettivo di apprendere la ricompensa umana sottostante a partire da traiettorie influenzate dalle scelte umane. Questo metodo porta con se grosse sfide tra cui la difficoltà di recuperare feedback umano e la razionalità limitata delle decisioni umane.
Oltre a Reinforcement Learning with Human Feedback sono presenti anche metodi come il DPO: [Direct Preference Optimization](https://arxiv.org/abs/2305.18290). DPO è un metodo innovativo progettato per semplificare il processo di fine-tuning rispetto a RLHF, nello specifico va a rimuovere la necessità di RLHG di utilizzare un reward model.

Il campo di ricerca è in fermento e bisogna considerare la possibilità che metodi ancora più efficienti (per il fine-tuning, come anche per modelli pre-addestrati) spuntino durante il corso dei lavori. Un esempio molto recente di un metodo innnovativo di fine tuning è quello presentato in un paper sul [self rewarding](https://arxiv.org/abs/2401.10020), in cui il reward model viene iterativamente migliorato. 

Oltre a tecniche di fine-tuning sono emerse anche molte tecniche di efficientamento di uso delle risorse durante il processo di fine-tuning. Tra queste è importante notare LOw-Rank Adaptation ([lora paper](https://arxiv.org/abs/2106.09685)) in cui solo alcuni parametri finali vengono aggiornati al fine di migliorare il comportamento della LLM in inferenza. 
Questa tecnica è stata inoltre adatta per supportare la capacità di quantizzazione dei parametri senza grosse perdite in performance post fine-tuning nel paper QLORA ([qlora paper](https://arxiv.org/abs/2305.14314)).

Un esempio pratico di come è possibile eseguire il fine-tuning di un modello LLaMa2 è disponibile SUL [blog di Maxime Labonne](https://mlabonne.github.io/blog/posts/A_Beginners_Guide_to_LLM_Finetuning.html)


### RAG vs FineTuning
Molto importante rispetto al nostro contesto è l'articolo [RAGvsFineTuning](https://arxiv.org/abs/2401.08406). Esso non solo espone delle differenze in performance in base all'applicazione di RAG, fine-tuning o entrambi, ma provvede molti spunti. 
Tra questi la metodologia utilizzata per selezionare e pulire materiale rilevante per il fine-tuning e metodi di valutazione automatica della performance dei modelli. 
Citando le loro osservazioni riguardo ai metodi RAG e FineTUning sul caso specifico trattato (Argicoltura): RAG was shown to be highly effective in instances where
 data is contextually relevant, such as in the interpretation of farm data, while also leading to more succinct
 responses than the base model. Fine-tuning, on the other hand, was found to be useful in teaching the model
 new skills specific to the agricultural domain, and providing more precise and succinct responses

Questo confronto tra RAG e fine-tuning evidenzia due metodologie complementari per migliorare le prestazioni degli LLM in applicazioni specifiche, potenzialmente entrambi applicabili in una webapp per indicazioni di spostamento. 




