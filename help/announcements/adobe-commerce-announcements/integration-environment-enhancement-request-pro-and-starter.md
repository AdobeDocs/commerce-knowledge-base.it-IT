---
title: Richiesta di miglioramento dell’ambiente di integrazione - Pro e Starter
description: Se sei un cliente Adobe Commerce su infrastruttura cloud con architettura Pro e al momento utilizzi ambienti di integrazione di dimensioni standard, o sei un cliente Adobe Commerce su infrastruttura cloud con architettura di pianificazione Starter e al momento utilizzi l’ambiente di staging di dimensioni standard e desideri maggiore potenza, puoi richiedere un aggiornamento agli ambienti di integrazione avanzata, che forniscono prestazioni quattro volte superiori. Questo articolo separa le istruzioni per i clienti Pro dai clienti Starter.
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# Richiesta di miglioramento dell’ambiente di integrazione - Pro e Starter

Se sei un cliente Adobe Commerce su infrastruttura cloud con architettura Pro e al momento utilizzi ambienti di integrazione di dimensioni standard, o sei un cliente Adobe Commerce su infrastruttura cloud con architettura di pianificazione Starter e al momento utilizzi l’ambiente di staging di dimensioni standard e desideri maggiore potenza, puoi richiedere un aggiornamento agli ambienti di integrazione avanzata, che forniscono prestazioni quattro volte superiori. Questo articolo separa le istruzioni per i clienti Pro dai clienti Starter.

>[!NOTE]
>
> L’aggiornamento a Integrazione avanzata potrebbe non risolvere tutti i problemi di prestazioni, in quanto dipenderebbe dai requisiti di risorse totali dell’installazione, incluse integrazioni o personalizzazioni di terze parti.
>
> È inoltre necessario assicurarsi di seguire le best practice per ottenere le migliori prestazioni nell’ambiente di integrazione, e anche questo potrebbe non essere una soluzione completa. Per informazioni, consulta la seguente documentazione: [Architettura Pro](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment) e [Architettura Starter](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment) nella Guida all&#39;infrastruttura cloud di Commerce.

## Pro

1. Se usi Pro, per eseguire l&#39;aggiornamento devi ridurre il numero di rami di integrazione a due (**il ramo di integrazione principale è incluso nel totale**). **Nota: non contare il ramo principale in questo totale. Il ramo principale non è considerato un ramo di integrazione.** Segui i passaggi descritti in [Gestire i rami con Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) nella documentazione per sviluppatori.
1. Il commerciante deve [inviare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) richiedendo un aggiornamento agli ambienti di integrazione avanzata, utilizzando il motivo del contatto &quot;*Richiedere una modifica alla configurazione cloud*&quot;.
1. Il team di progettazione clienti di Adobe conferma il numero di ambienti di integrazione e avvia la modifica.
1. Il commerciante verrà informato nel ticket quando l’aggiornamento sarà completato.
1. Il commerciante ridistribuisce gli ambienti di integrazione. Segui i passaggi descritti in [Unire un ramo](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) nella documentazione per sviluppatori. *Nota*: la distribuzione viene eseguita automaticamente quando si esegue: <pre>origine git push &lt;branch-name></pre>

Un aumento delle prestazioni indica un aggiornamento riuscito agli ambienti di integrazione avanzata.

**Note**:

* Le dimensioni standard e le dimensioni migliorate sono le uniche due dimensioni disponibili.
* Tutti gli ambienti di integrazione per un determinato archivio hanno le stesse dimensioni; non possono essere dimensionati in modo indipendente.
* Se hai bisogno di più di due degli ambienti di integrazione avanzata, consulta il team del tuo account Adobe.

## Starter

1. I piani iniziali non possono avere rami di integrazione: i commercianti devono eliminare gli ambienti di integrazione e lasciare solo l’ambiente di staging. Segui i passaggi descritti in [Gestire i rami con Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) nella documentazione per sviluppatori. Il numero di ambienti disponibili verrà ridotto per consentire al massimo un ambiente di integrazione.
1. Il commerciante deve [inviare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) richiedendo un aggiornamento agli ambienti di integrazione avanzata, utilizzando il motivo di contatto *&quot;Richiedere una modifica alla configurazione cloud&quot;* - **l&#39;ambiente di staging è un ambiente di integrazione denominato**.
1. Il team di progettazione clienti di Adobe conferma il numero di ambienti di integrazione e avvia la modifica.
1. Il commerciante verrà informato nel ticket quando l’aggiornamento sarà completato.
1. Il commerciante ridistribuisce gli ambienti di integrazione. Segui i passaggi descritti in [Unire un ramo](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches#merge-a-branch) nella documentazione per sviluppatori. *Nota*: la distribuzione viene eseguita automaticamente quando si esegue: <pre>origine git push &lt;branch-name></pre>

Un aumento delle prestazioni indica un aggiornamento riuscito agli ambienti di integrazione avanzata.

**Note**:

* Le dimensioni standard e le dimensioni migliorate sono le uniche due dimensioni disponibili.
* Tutti gli ambienti di integrazione per un determinato archivio hanno le stesse dimensioni; non possono essere dimensionati in modo indipendente.
* Se hai bisogno di ambienti di integrazione diversi da quelli di staging, consulta il team del tuo account Adobe.
* Se l’acquisto viene effettuato dopo il 17 settembre 2020, questo miglioramento non sarà applicabile a causa dell’ampliamento degli ambienti di integrazione.
