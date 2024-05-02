---
title: "Impossibile eliminare il file. Attenzione! scollega: errore di file o directory non presente nel [!DNL Admin]"
description: Questo articolo fornisce una soluzione al problema in cui viene visualizzato un errore *Il file non può essere eliminato. Avviso!scollega errore di file o directory non presente* dal [!DNL Admin] quando si esegue una [!DNL Javascript/CSS] scarica.
feature: Admin Workspace, Observability
role: Developer
exl-id: db265e3c-a809-4404-839a-273001e81d22
source-git-commit: fd5fd6e1bc04db56497a2e0c2a96bc1b06d4f7a1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# *Impossibile eliminare il file. Attenzione!unlink: errore di file o directory non presente* dal [!DNL Admin]

Questo articolo fornisce una soluzione al problema in cui viene visualizzato un errore *Impossibile eliminare il file. Attenzione!unlink: errore di file o directory non presente* dal [!DNL Commerce Admin] quando si esegue una [!DNL JavaScript/CSS] scarica.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.0 - 2.4.6, tutti i metodi di implementazione

## Problema

Si verifica un errore quando si esegue una [!DNL JS/CSS] scarica:

*Impossibile eliminare il file &quot;/app/pub/static/_cache/merge/.nfsa42d0e64799fd1000000001b&quot;. Avviso!unlink(/app/pub/static/_cache/merge/.nfsa42d0e64799fd1000000001b): file o directory non presente*

Oppure: l’errore riportato sopra viene visualizzato nel [!DNL Admin]e/o un errore simile in [!DNL New Relic] o nei registri di distribuzione.

Oppure: non è possibile accedere alla funzione di reporting avanzato e il processo cron analytics_collect_data ha esito negativo con questo errore:

*Il file &quot;/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0&quot; non può essere eliminato. Avviso!unlink(/app/var/tmp/analytics/tmp/.nfsb3b6041dd44588a0000850c0): file o directory non presente*

<u>Passaggi da riprodurre:</u>

Metodo 1:

1. Accedi a [!DNL Admin].
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Clic **[!UICONTROL Flush][!DNL JavaScript/CSS][!UICONTROL Cache]**.

Metodo 2:

1. Accedi a [!DNL Admin].
1. Vai a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Apporta le modifiche al [!UICONTROL Base URL] o [!UICONTROL Base URL (Secure)].
1. Fai clic su **[!UICONTROL Save Config]**.

## Soluzione

Se utilizzi l’infrastruttura Adobe Commerce on Cloud e hai [!DNL magento/magento-cloud-patches] 1.0.22 che include la patch, non è necessario installare separatamente ACSD-50165.

Infrastruttura Adobe Commerce on Cloud: aggiornamento delle patch cloud per Commerce al 1.0.22 (**o più recente**) che contiene questa correzione: [Patch cloud per Commerce](/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).

Adobe Commerce on-premise: applica ACSD-50165 utilizzando [Strumenti patch di qualità > Utilizzo](/docs/commerce-operations/tools/quality-patches-tool/usage.html). La patch ACSD-50165 viene fornita con [!DNL QPT] [v1.1.30.](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html#v1-1-30)

## Lettura correlata

* [[!DNL Quality Patches Tool] > Note sulla versione](/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) nella guida Strumenti di Commerce.
* [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida Strumenti di Commerce.
