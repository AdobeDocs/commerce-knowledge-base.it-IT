---
title: Test rapido in produzione se un sito live utilizza lo stesso dominio
description: Se disponi di un sito live in esecuzione sul dominio di produzione ("example.com") e hai bisogno di testare il nuovo store sull’ambiente di produzione dell’infrastruttura cloud di Adobe Commerce con Fastly CDN abilitato, ti consigliamo di utilizzare il sottodominio (come "prod.example.com"), dopo averlo aggiunto in precedenza a Fastly, per qualsiasi attività di test pre-avvio. Questo articolo illustra i dettagli e fornisce collegamenti utili alle relative risorse della documentazione di Adobe Commerce.
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Test rapido in produzione se un sito live utilizza lo stesso dominio

Se nel dominio di produzione (`example.com`) è in esecuzione un sito attivo e devi testare il nuovo archivio nell&#39;ambiente di produzione di Adobe Commerce sull&#39;infrastruttura cloud con Fastly CDN abilitato, ti consigliamo di utilizzare il sottodominio (come `prod.example.com`), dopo averlo aggiunto in precedenza a Fastly, per qualsiasi attività di test precedente all&#39;avvio. Questo articolo illustra i dettagli e fornisce collegamenti utili alle relative risorse della documentazione di Adobe Commerce.

## Problema

L&#39;archivio corrente che utilizza il dominio di produzione `example.com` è attivo e operativo. Tuttavia, devi testare il nuovo store, creato con Adobe Commerce sull’infrastruttura cloud e implementato nell’ambiente di produzione, con il servizio Fastly full page cache abilitato.

Il problema è che l&#39;ambiente di produzione del progetto di infrastruttura cloud di Adobe Commerce utilizza lo stesso dominio live (`example.com`) e non è possibile passare a questo dominio con il proprio archivio live corrente in esecuzione nello stesso dominio.

### Perché utilizzare Fastly per il test nell’ambiente di produzione?

In teoria, puoi saltare l’utilizzo di Fastly CDN e testare l’Adobe Commerce nell’archivio dell’infrastruttura cloud nell’ambiente di produzione senza la cache della pagina intera abilitata.

Tuttavia, con la cache a pagina intera abilitata, le prestazioni dello store sono diverse; non si conosce mai le prestazioni reali del sito se non lo si è testato con CDN prima dell’avvio. Testare il tuo store sulla produzione con Fastly CDN abilitato è il consiglio ufficiale di Adobe Commerce.

## Soluzione: utilizzare il sottodominio di produzione

Utilizza il sottodominio di primo livello (`prod.example.com`) per il nuovo archivio dell&#39;infrastruttura cloud di Adobe Commerce nell&#39;ambiente di produzione mantenendo il sito attivo corrente nel dominio di base (`example.com`).

Quando pianifichi il progetto Adobe Commerce su infrastruttura cloud, puoi specificare un sottodominio di produzione di questo tipo e richiedere al team di infrastruttura cloud di puntare il sottodominio al servizio Fastly.

Per elaborare il sottodominio all’interno del progetto di infrastruttura cloud di Adobe Commerce, segui la procedura riportata di seguito:

* [Invia un ticket di supporto](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) richiedendo di aggiungere il sottodominio alla configurazione Fastly Service/Nginx (per l&#39;architettura del piano Pro di Adobe Commerce on Cloud Infrastructure).
* Configura le impostazioni DNS corrispondenti sul tuo lato.

Dopo aver eseguito i passaggi per la configurazione del sottodominio, devi eseguire anche questi passaggi per convalidare il dominio di produzione per il certificato SSL:

* Carica il record TXT DNS per la convalida SSL del dominio di produzione.
* [Invia un ticket di supporto](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) richiedendo di convalidare il dominio di produzione per il certificato SSL.

L’utilizzo del sottodominio ti consente di eseguire un &quot;avvio morbido&quot; dello store in futuro, in quanto tale avvio richiede solo l’aggiornamento delle impostazioni DNS corrispondenti.

## Documentazione correlata

Nella nostra knowledge base di supporto:

* [Configurare le impostazioni DNS veloci negli ambienti di staging e produzione](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html?lang=it)
* [Imposta Fastly per il piano Starter sul cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/set-up-fastly-for-starter-plan-on-cloud.html?lang=it)
* [Potenziali blocchi per l&#39;avvio su Adobe Commerce nell&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html?lang=it)

Nella documentazione per gli sviluppatori:

* [Panoramica rapida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=it)
* [Elenco di controllo pubblicazione: configurazioni DNS per Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=it)
