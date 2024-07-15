---
title: "Impossibile eliminare il file. Attenzione! scollega: errore di file o directory non presente da  [!DNL Admin]"
description: Questo articolo fornisce una soluzione al problema in cui viene visualizzato un errore *Il file non può essere eliminato. Avviso!scollega errore di file o directory non presente* da  [!DNL Admin] quando esegui uno svuotamento di  [!DNL Javascript/CSS] .
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *Impossibile eliminare il file. Avviso!unlink: errore di file o directory non presente* da [!DNL Admin]

Questo articolo fornisce una soluzione al problema che causa un errore *Impossibile eliminare il file. Avviso!unlink: errore di file o directory* non presente in [!DNL Commerce Admin] durante uno scaricamento di [!DNL JavaScript/CSS].

## Prodotti e versioni interessati

* Adobe Commerce 2.4.0 - 2.4.6, tutti i metodi di implementazione

## Problema

Errore durante lo scaricamento di [!DNL JS/CSS]:

*Impossibile eliminare il file &quot;/app/pub/static/_cache/merge/.nfsa42d0e64799fd1000000001b&quot;. Avviso!unlink(/app/pub/static/_cache/merge/.nfsa42d0e64799fd1000000001b): file o directory non esistente*

Oppure: l&#39;errore sopra riportato viene visualizzato in [!DNL Admin] e/o un errore simile in [!DNL New Relic] o nei registri di distribuzione.

Oppure: non è possibile accedere alla funzione di reporting avanzato e il processo cron analytics_collect_data ha esito negativo con questo errore:

*Impossibile eliminare il file &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0&quot;. Avviso!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0): file o directory non esistente*

<u>Passaggi da riprodurre:</u>

Metodo 1:

1. Accedere a [!DNL Admin].
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Fare clic su **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

Metodo 2:

1. Accedere a [!DNL Admin].
1. Vai a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Apportare modifiche a [!UICONTROL Base URL] o [!UICONTROL Base URL (Secure)].
1. Fai clic su **[!UICONTROL Save Config]**.

## Soluzione

Se ti trovi nell&#39;infrastruttura Adobe Commerce on Cloud e hai installato [!DNL magento/magento-cloud-patches] 1.0.22 che include la patch, non è necessario installare separatamente ACSD-50165.

Infrastruttura Adobe Commerce on Cloud: aggiornamento delle patch cloud per Commerce al 1.0.22 (**o successivo**) che contiene questa correzione: [Patch cloud per Commerce](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce on-premise: applica ACSD-50165 utilizzando [Strumenti patch di qualità > Utilizzo](/docs/commerce-operations/tools/quality-patches-tool/usage.html). La patch ACSD-50165 viene fornita con [!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## Lettura correlata

* [[!DNL Quality Patches Tool] > Note sulla versione](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) nella guida degli strumenti di Commerce.
* [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida degli strumenti di Commerce.
