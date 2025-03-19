---
title: Accesso [!UICONTROL Admin] non funzionante - dimensione massima sessione consentita superata
description: Risolvere il problema quando si tenta di accedere al pannello [!UICONTROL Admin] e il modulo viene aggiornato, rendendo impossibile l'accesso.
exl-id: 12789df0-6130-4e60-a92a-68ed329bd7fd
source-git-commit: fe4a48581bdfe24da5082b69fb26a8032bd77334
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# Accesso [!UICONTROL Admin] non funzionante - dimensione massima sessione consentita superata

In questo articolo viene fornita una correzione per i casi in cui si tenta di accedere al pannello [!UICONTROL Admin], ma il modulo viene appena aggiornato e non è possibile effettuare l&#39;accesso oppure si eseguono alcune azioni nel pannello [!UICONTROL Admin] e si esce automaticamente.
La causa è il superamento di [!UICONTROL Admin] [!UICONTROL Session Size].

## Versioni interessate

* Adobe Commerce on-premise, [tutte le versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Problema

Si verifica uno dei seguenti sintomi in [!UICONTROL Admin]:

1. Impossibile accedere a [!UICONTROL Admin] perché il modulo continua a essere ricaricato.
1. Ti disconnetti automaticamente quando tenti di eseguire un&#39;azione.

## Causa

È stata superata la dimensione massima consentita per la sessione.

## Soluzione

Verificare nel file `var/log/support_report.log` la presenza di errori di questo tipo:

Rapporto *[2023-07-13T04:26:09.792060+00:00].AVVISO: la dimensione della sessione di 260572 ha superato la dimensione massima di 256000 consentita per la sessione. [] []
[2023-07-13T04:26:17.056714+00:00] report.AVVISO: la dimensione della sessione di 260570 ha superato la dimensione massima di 256000 consentita per la sessione. [][]*

Se si verificano questi errori, la soluzione sarà:

<u>Adobe Commerce locale</u>:
1. Aumentare il valore **[!UICONTROL Max Session Size in Admin]** dalla configurazione back-end. A tale scopo, passare a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Security]** > **[!UICONTROL Max Session Size in Admin]**.
1. Imposta il valore su *500000* o versione successiva. A seconda della dimensione massima esistente segnalata nell&#39;errore, è possibile impostare il valore su *0*, che rimuoverà il limite di dimensione della sessione.

<u>Adobe Commerce sull&#39;infrastruttura cloud</u>:

Questa impostazione è accessibile solo in [!UICONTROL Admin] quando la modalità di distribuzione/operazione è *default* o *developer*. Tuttavia, nell’ambiente cloud è consentita solo la modalità di distribuzione Produzione.)

Per aumentare questo valore, esegui questo comando nel terminale (SSH):

```ssh
bin/magento config:set system/security/max_session_size_admin 500000
```

È possibile impostare un valore superiore a *500000* a seconda delle dimensioni massime esistenti segnalate nell&#39;errore e impostare il valore su *0* per rimuovere il limite delle dimensioni della sessione.

## Lettura correlata

* [Dimensione sessione](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management#admin-sessions) nella Guida di Admin Systems
* [Modalità operativa](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/set-mode) nella Guida alla configurazione
* [Connessioni sicure](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections) nella Guida di Commerce on Cloud Infrastructure
