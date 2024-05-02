---
title: "ACSD-54961: l’utente amministratore con restrizioni non può eseguire aggiornamenti di massa [!UICONTROL Product Review status]"
description: Applica la patch ACSD-54961 per risolvere il problema di Adobe Commerce per cui un utente amministratore con restrizioni non può aggiornare in massa lo stato di recensione del prodotto.
feature: Products
role: Admin, Developer
exl-id: 26c5bacd-21de-4533-a7b6-4acbacd38fec
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54961: l’utente amministratore con restrizioni non può eseguire aggiornamenti di massa [!UICONTROL Product Review status]

La patch ACSD-54961 risolve il problema che impediva l’aggiornamento in massa di un utente amministratore con restrizioni [!UICONTROL Product Review status]. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-54961. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un utente amministratore con restrizioni non può eseguire un aggiornamento di massa [!UICONTROL Product Review status].

<u>Passaggi da riprodurre</u>:

1. Crea una visualizzazione aggiuntiva per sito Web, store e store.
1. Aggiungere un prodotto al secondo store, quindi aggiungere una recensione.
1. Crea un utente amministratore con restrizioni con accesso solo al secondo archivio.
1. Accedi come utente amministratore con restrizioni, quindi vai a **[!UICONTROL  Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]**, e impostare **Stato** a *Approvato* o *In sospeso*.

<u>Risultati previsti</u>:

L’utente amministratore con restrizioni può aggiornare le recensioni utilizzando **[!UICONTROL Mass Update]** azione.

<u>Risultati effettivi</u>:

Si verifica un errore durante l’aggiornamento delle revisioni tramite **[!UICONTROL Mass Update]** azione.<br>
Il `var/log/exception.log` contiene un errore simile:

```
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
