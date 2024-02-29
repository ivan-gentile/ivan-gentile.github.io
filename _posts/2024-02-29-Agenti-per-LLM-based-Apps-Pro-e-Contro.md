---
title:  "Agenti per LLM-based Apps Pro e Contro"
image : "/assets/images/post/voyager.png"
author: "Ivan Gentile"
date: 2024-02-29 00:13:58 +0600
description: "Esploriamo come gli agenti basati su Large Language Models (LLM) stanno trasformando e mettendo in pericolo le applicazioni web"
tags: [AI, LLM, Neural Networks, RAG, Retrieval Augmented Generation, Web Applications, Cybersecurity, Prompt Injection, Human-in-the-Loop]
---

## Definizione di agente

Una qualsiasi entità che può percepire il suo ambiente tramite sensori e agire su quell'ambiente tramite attuatori. Nel contesto degli LLM, un agente può essere inteso come il sistema che, date istruzioni in linguaggio naturale, interagisce con altri sistemi per portare a termine le istruzioni ottenute autonomamente.

Un ottimo esempio è [Voyager](), un agente incarnato in un ambiente virtuale che dimostra comportamenti autonomi emergenti ed evolutivi 

## I pro di integrare agenti in una app

Gli agenti basati su Large Language Models (LLM) sfruttano la loro estesa base di conoscenza, derivata da vasti set di dati, per arricchire l'esperienza degli utenti e possono essere in diverse tipologie di applicazioni web. 

Per l'integrazione degli agenti LLM in applicazioni web, sono disponibili diversi framework e strumenti. Framework open-source come [LangChain](https://www.langchain.com/) supportano lo sviluppo di applicazioni LLM in linguaggi come Python e JavaScript, facilitando il passaggio da prototipi a soluzioni produttive.

Un approccio guidato alla creazione di applicazioni che incorporano agenti LLM include la gestione di componenti chiave quali il core dell'agente, il modulo di memoria, gli strumenti dell'agente e i moduli di pianificazione. Framework quali LangChain, oltre a strumenti aggiuntivi, giocano un ruolo cruciale nell'integrazione di funzionalità avanzate come moduli di memoria, l'accesso a strumenti di terze parti e meccanismi efficaci di recupero dati. Un ottimo blogpost per fare pratica è [questo](https://developer.nvidia.com/blog/building-your-first-llm-agent-application/) sul sito di NVIDIA

Il tema degli agenti rimane un tema di ricerca \footnote{e di interesse, la repo \url{https://github.com/Significant-Gravitas/AutoGPT} è tra quelle con la crescita più rapida di sempre} molto caldo, un articolo interessante a riguardo è [More agents is all you need](https://arxiv.org/abs/2402.05120), con la associata [repo con codice](https://anonymous.4open.science/)


## I problemi di sicurezza, contro

Questi agenti, capaci di comprendere e agire su istruzioni in linguaggio naturale, promettono di rivoluzionare il modo in cui interagiamo con il mondo virtuale. Tuttavia, con grandi potenzialità arrivano grandi sfide, specialmente in termini di sicurezza.

La sicurezza, quando si parla di integrazione di agenti LLM in applicazioni sensibili come i browser web, non può essere trascurata. Come dimostrato da recenti studi, i rischi di iniezione di prompt possono portare a conseguenze indesiderate, da violazioni della privacy a veri e propri attacchi informatici. È quindi imperativo che gli sviluppatori adottino strategie di mitigazione efficaci.

Nello specifico uno degli attacchi più comuni a llm-based applications è quello del **prompt injection**. OWASP ha un [ottimo documento](https://owasp.org/www-project-top-10-for-large-language-model-applications/) per riuscire a farsi un'idea più formata sull'argomento. 

Per citare un esempio illuminante di integrazione sicura di agenti possiamo parlare di filtri di input rigorosi e sistemi di approvazione umana. Questi strumenti consentono di limitare i caratteri accettati dagli input degli utenti e soprattuto l'inserire l'umano nel loop, ovvero di richiedere l'approvazione umana per azioni critiche è essenziale per ridurre significativamente il rischio di attacchi malevoli.
Donato Capitella ha scritto un ottimo [articolo](https://labs.withsecure.com/publications/browser-agents-llm-prompt-injection?utm_source=linkedin&utm_medium=organic-social&utm_campaign=gl-consulting-blog-chatgpt) a riguardo.

Inoltre, la collaborazione tra sviluppatori e ricercatori è fondamentale per sviluppare soluzioni innovative che garantiscano la sicurezza degli utenti senza compromettere la funzionalità o l'esperienza utente. Progetti di ricerca attuali stanno esplorando nuove tecniche di rilevazione degli attacchi e metodi per rafforzare la sicurezza degli agenti LLM, promettendo avanzamenti significativi in questo campo.

In conclusione, mentre ci avventuriamo nell'integrazione degli agenti LLM nelle nostre applicazioni web, dobbiamo rimanere vigili sui rischi di sicurezza associati. Attraverso l'adozione di strategie di mitigazione adeguate e la collaborazione tra comunità di sviluppatori e ricercatori, possiamo assicurare che l'evoluzione degli agenti LLM proceda in modo sicuro e benefico per tutti. Il futuro degli agenti LLM nelle applicazioni web è brillante, ma solo con un approccio consapevole e proattivo alla sicurezza possiamo navigare con successo le sue acque.