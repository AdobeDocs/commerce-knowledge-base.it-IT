---
title: '[!DNL Admin] accesso non funzionante - dimensione massima sessione consentita superata'
description: Risolvi il problema quando tenti di accedere al tuo [!DNL Admin] e il modulo si aggiorna. Impossibile effettuare l’accesso.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: 8718148f6d9a40c9a71484a7fbc818a626e825e1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# [!DNL Admin] accesso non funzionante - dimensione massima sessione consentita superata

Questo articolo corregge i problemi di accesso a [!DNL Admin] ma il modulo si aggiorna e non puoi accedere. Questo perché il [!DNL Admin] Dimensione sessione superata.

## Versioni interessate

* Adobe Commerce on-premise [tutte le versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce sull’infrastruttura cloud, [tutte le versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Impossibile accedere a [!DNL Admin], perché il modulo viene ricaricato.

## Causa

È stata superata la dimensione massima consentita per la sessione.

## Soluzione

Controlla la `var/log/support_report.log` file per gli errori di questo tipo:

*[13T04/07/2023:26:9.792060+00:00] report.WARNING: La dimensione della sessione di 260572 ha superato la dimensione massima di 256000 consentita per la sessione. [] []
[13T04/07/2023:26:17.056714+00:00] report.WARNING: La dimensione della sessione di 260570 ha superato la dimensione massima di 256000 consentita per la sessione. [][]*

Se si verificano questi errori, la soluzione sarà:

<u>Adobe Commerce on-premise</u>:
1. Aumenta **[!UICONTROL Max Session Size in Admin]** dalla configurazione back-end. Per farlo, vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. Imposta il valore su *500000* o superiore. A seconda della dimensione massima esistente segnalata nell’errore, puoi anche impostare il valore su *0* che rimuoverà il limite di dimensione della sessione.

<u>Adobe Commerce sull’infrastruttura cloud</u>:

(questa impostazione è accessibile solo in [!DNL Admin] quando la modalità di distribuzione/operazione è predefinita per sviluppatore. Tuttavia, nell’ambiente Cloud è consentita solo la modalità di distribuzione Produzione.)

Per aumentare questo valore, esegui questo comando nel terminale (SSH):

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

Puoi impostare su un valore superiore a *500000* a seconda della dimensione massima esistente segnalata nell’errore e puoi anche impostare il valore su *0* per rimuovere il limite di dimensione della sessione.

## Lettura correlata

* [Dimensione sessione](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions) nella Guida ai sistemi di amministrazione.
* [Modalità operativa](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode) nella Guida alla configurazione.
* [Connessioni sicure](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) nella Guida all’infrastruttura cloud di Commerce.
