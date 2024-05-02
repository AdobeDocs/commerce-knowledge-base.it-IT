---
title: Domande frequenti sui criteri del ciclo di vita aggiornati per le versioni di Adobe Commerce
description: "Adobe Commerce fornisce correzioni di qualità per una versione secondaria per un minimo di 12 mesi dalla data di disponibilità generale della successiva versione software secondaria. Il modo in cui forniamo correzioni di qualità durante questo periodo sta cambiando:"
exl-id: 4aa601d0-ee1d-4f1f-a684-188772a58dd1
feature: Compliance, Support
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '1176'
ht-degree: 0%

---

# Domande frequenti sui criteri del ciclo di vita aggiornati per le versioni di Adobe Commerce

## Cosa sta cambiando?

Adobe Commerce fornisce correzioni di qualità per una versione secondaria per un minimo di 12 mesi dalla data di disponibilità generale della successiva versione software secondaria. Il modo in cui forniamo correzioni di qualità durante questo periodo sta cambiando:

* **Criteri precedenti:** Attualmente le correzioni di qualità alla riga precedente nella finestra EOS di 12 mesi vengono distribuite tramite il rilascio di patch trimestrali, rendendo quindi le patch trimestrali una combinazione di sicurezza + qualità.
* **Nuovo criterio:** A partire dalla versione 2.4 come versione secondaria più recente, le patch di rilascio per la versione supportata precedente (2.3) passeranno alla sola protezione. Continueremo a fornire correzioni di qualità per la precedente linea supportata durante la finestra di 12 mesi dopo il rilascio di una linea secondaria (come 2.4) e successive linee di rilascio secondarie; ma queste saranno rese disponibili tramite [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) ed essere concentrati solo su problemi critici.

## Quando ha effetto questo criterio?

La versione 2.3.6 di Adobe Commerce è pianificata per il 15 ottobre 2020 ed è l’ultima patch per Adobe Commerce 2.3 che includerà sia qualità che sicurezza. Dopo la versione 2.3.6, la linea 2.3.x diventerà di sola sicurezza e i problemi critici relativi alla qualità per la versione 2.3 possono essere risolti tramite QPT.

>[!NOTE]
>
>L&#39;unica volta che rilasceremo una versione completa di 2.3 è se dobbiamo mantenere la conformità con il nostro stack tecnologico, come per PHP o Elasticsearch. Questo accade nel secondo trimestre del 2021 con un aggiornamento obbligatorio di PHP 7.4, aumenteremo la linea a 2.3.7. Per ulteriori informazioni, consulta [Supporto PHP 7.4 per la versione di Adobe Commerce 2.3.x](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) Post di DevBlog.

## Cos’è una versione di sola sicurezza?

Le versioni con solo protezione contengono solo correzioni di protezione e non è stata corretta alcuna qualità. Tieni presente, tuttavia, che le nostre versioni di sicurezza possono includere hotfix specifici quando li consideriamo assolutamente critici per l’esecuzione di Adobe Commerce.

## Sarà ancora disponibile una versione con sola protezione per l’ultima riga (dalla pubblicazione, versione 2.4)?

Adobe continuerà a disporre di versioni di sola sicurezza per la riga dell’ultima versione. La procedura per tali operazioni è descritta in [Introduzione alla nuova versione delle patch di sicurezza](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287) Post di DevBlog.

## Che cos&#39;è lo strumento Patch di qualità?

Consulta la sezione [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) articolo della knowledge base di supporto.

## Chi dovrebbe considerare l’utilizzo di questo nuovo criterio?

La nuova politica è destinata a creare percorsi che consentano ai commercianti di pianificare in modo strategico i costi di sviluppo annuali di Adobe Commerce, consentendo loro di mantenere la sicurezza e la qualità critica durante questi cicli strategici. Può essere utilizzato anche dai commercianti che si preoccupano della sicurezza su tutto il resto e sono generalmente soddisfatti della stabilità della linea più vecchia e supportata. Gli esercenti potrebbero trovare più facile pianificare e preventivare questi aggiornamenti in quanto saranno più prevedibili.

## I commercianti devono effettuare l’aggiornamento all’ultima linea?

In ultima analisi, tutti i commercianti devono ancora dare priorità alla pianificazione per adottare l’ultima linea di Adobe Commerce in modo tempestivo. La nuova linea Security Only e il nuovo strumento QPT non intendono sostituire la roadmap di aggiornamento strategico per i commercianti, ma offrono flessibilità ai commercianti nella pianificazione della roadmap di aggiornamento e un mezzo per reagire rapidamente a problemi di sicurezza/qualità senza dover implementare un intero aggiornamento.

## Come è possibile ottenere correzioni di qualità per le versioni secondarie supportate che non sono la riga più recente?

Le correzioni saranno rese disponibili tramite [Strumento Patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).

## Come si ottengono correzioni di qualità sull’ultima riga?

La riga corrente avrà qualità come parte dell’aggiornamento trimestrale. Tra una versione e l’altra, se contatti il supporto per una correzione sulla riga più recente, la fornirà tramite QPT. Quindi, una volta effettuato l’aggiornamento alla versione contenente la correzione, questa verrà applicata tramite la patch trimestrale.

## Quali problemi di qualità verranno risolti nelle versioni secondarie supportate che non sono l’ultima riga?

Solo i principali problemi di qualità che interrompono i flussi core verranno risolti nella riga precedente (2.3) e consegnati tramite QPT.

## Eventuali correzioni di qualità faranno parte della versione trimestrale per le versioni secondarie supportate che non sono l’ultima riga?

Sì, come parte della riga dedicata esclusivamente alla sicurezza, vengono rilasciati gli Adobi che chiamano &quot;hotfix&quot; a tale riga; si tratta di problemi altamente critici che interessano l’applicazione Adobe Commerce.

## I miglioramenti della sicurezza e i QPT verranno consegnati contemporaneamente?

La riga solo titolo seguirà il programma di rilascio trimestrale e verrà rilasciata con la nomenclatura -p1. Esempio 2.3.6-p1. La qualità verrà rilasciata ad hoc man mano che i problemi di qualità vengono rilevati e risolti e saranno resi disponibili tramite QPT.

## Cosa devo fare se si verifica un problema di qualità che non viene risolto nelle versioni secondarie supportate che non sono l’ultima riga o QPT?

Il vantaggio principale della sicurezza è la sicurezza della linea precedente. Tramite QPT verranno rese disponibili solo le patch per problemi importanti che interrompono i flussi core.

I problemi che non influiscono sui flussi core o hanno soluzioni alternative verranno risolti solo nella riga più recente. Adobe incoraggia coloro che desiderano apportare correzioni critiche e non critiche a passare alla riga più recente.

## Gli upgrade saranno più costosi o più difficili per i commercianti se rimangono sulla linea di sicurezza fino alla fine del supporto di sicurezza?

In teoria, dovrebbero essere uguali in termini di costo per il commerciante in termini di ore di sviluppo, a condizione che non abbiano adottato un gran numero di patch di qualità. Se un esercente trova che necessiti o desideri più di una manciata di patch tramite lo strumento QPT, si consiglia di dare priorità a un aggiornamento alla versione più recente di Adobe Commerce. L’adozione di un numero elevato di patch di qualità, invece di eseguire l’aggiornamento alla versione corrente di Adobe Commerce, può aumentare i costi di sviluppo e la complessità dell’aggiornamento una volta che la linea dedicata esclusivamente alla sicurezza raggiunge la fine del supporto.

## Perché devo limitare la quantità di patch di qualità distribuite tramite QPT?

Applicando molte singole correzioni di qualità, il codice Adobe Commerce diventa più complesso. La complessità aggiunta potrebbe causare modifiche imprevedibili durante l’aggiornamento alla riga di rilascio più recente. Per questo motivo consigliamo di utilizzare QPT con moderazione e solo per le correzioni più critiche.

## E per quanto riguarda la conformità per gli stack tecnologici?

Durante il ciclo di vita di una linea di rilascio ci saranno aggiornamenti a vari stack di tecnologia come PHP o Elasticsearch che dovranno essere aggiornati per rimanere conformi. Daremo ai nostri commercianti il massimo preavviso possibile che questi stanno arrivando.

Nota: nel secondo trimestre del 2021, dovremo aggiornare PHP e Redis sulla linea 2.3.x per rimanere conformi. In questo modo la linea verrà incrementata a 2.3.7. Per ulteriori informazioni, consulta [Supporto PHP 7.4 per la versione di Adobe Commerce 2.3.x](https://community.magento.com/t5/Magento-DevBlog/PHP-7-4-support-for-Magento-2-3-x-release-line/ba-p/458946) Post di DevBlog.
