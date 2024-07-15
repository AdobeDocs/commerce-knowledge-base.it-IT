---
title: Errore 404 not found durante l'accesso a Configurazione guidata Web tramite il pannello di amministrazione
description: Questo articolo fornisce una soluzione per l'errore 404 non trovato che si verifica quando si tenta di accedere all'Impostazione guidata Web tramite il pannello di amministrazione.
exl-id: 1b89da58-c872-481b-b2a0-aa48db8223db
feature: Admin Workspace, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Errore 404 not found durante l&#39;accesso a Configurazione guidata Web tramite il pannello di amministrazione

Questo articolo fornisce una soluzione per l&#39;errore 404 non trovato che si verifica quando si tenta di accedere all&#39;Impostazione guidata Web tramite il pannello di amministrazione.

## Prodotti e versioni interessati

* La funzionalità Installazione guidata Web è stata rimossa nella versione 2.3.6 di Adobe Commerce (tutti i metodi di distribuzione) ed è stata rimossa nella versione 2.4.0.

## Problema

Quando si installa un’estensione tramite la procedura guidata di installazione Web, viene visualizzata una pagina 404.

<u>Passaggi da riprodurre</u>:

Il commerciante fa clic su Installazione guidata Web per installare un nuovo modulo/integrazione.

<u>Risultato previsto</u>:

Installazione di moduli/integrazioni.

<u>Risultato effettivo</u>:

Viene visualizzato un errore 404.

## Causa

L&#39;Impostazione guidata Web è stata disabilitata per tutte le istanze di Adobe Commerce sull&#39;infrastruttura cloud. Non è possibile abilitarla. Le estensioni devono essere installate tramite Compositore.

## Soluzione

Questa funzione è disabilitata in Adobe Commerce sull’infrastruttura cloud.

Consulta [Installare, gestire e aggiornare le estensioni](https://devdocs.magento.com/cloud/howtos/install-components.html) nella documentazione per gli sviluppatori per informazioni su come eseguire aggiornamenti o installare moduli esterni per Adobe Commerce nell&#39;infrastruttura cloud.
Consulta [Installazione rapida](https://devdocs.magento.com/guides/v2.3/install-gde/composer.html) nella documentazione per gli sviluppatori per informazioni su come eseguire aggiornamenti o installare moduli esterni per Adobe Commerce on-premise.

## Lettura correlata

* Consulta [Installare un&#39;estensione](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension) nella documentazione per gli sviluppatori.
