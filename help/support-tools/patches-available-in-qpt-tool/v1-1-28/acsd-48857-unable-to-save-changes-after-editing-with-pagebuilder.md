---
title: '"ACSD-48857: impossibile salvare le modifiche dopo la modifica con [!DNL Page Builder]'''
description: Applica la patch ACSD-48857 per risolvere il problema di Adobe Commerce, se l’utente non è in grado di salvare le modifiche dopo la modifica con [!DNL Page Builder].
exl-id: c95b354d-8954-4e9c-9e92-8a64f62f0a68
feature: Admin Workspace, CMS, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-48857: impossibile salvare le modifiche dopo la modifica con [!DNL Page Builder]

La patch ACSD-48857 risolve il problema se l’utente non è in grado di salvare le modifiche dopo averle modificate con [!DNL Page Builder]. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-48857. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente non è in grado di salvare le modifiche dopo averle modificate con [!DNL Page Builder].

<u>Passaggi da riprodurre</u>

1. Accedi al sito web dell’amministratore.
1. Accedi a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** per creare una pagina CMS vuota.
1. Esegui questo script SQL per impostare quanto segue **[!UICONTROL Content]** valore campo:

   ```SQL
   update cms_page set content = '<div data-content-type="text" data-appearance="default" data-element="main"><h4 style="text-align: center;" contenteditable="true" data-placeholder="Edit Heading Text" data-content-type="heading" data-appearance="default" data-element="main">THE RULES</h4></div>' where page_id=8;
   ```

1. Torna a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** in Admin.
1. Modifica la pagina.
1. Vai a **[!UICONTROL Content]** scheda.
1. Clic **[!UICONTROL Save]**.

<u>Risultati previsti</u>

È stata implementata l’eliminazione dei contenuti HTML. Rimuove [!DNL Page Builder] attributi HTML riservati nei contenuti generati dall’editor di testo.

<u>Risultati effettivi</u>

La pagina non viene salvata e il caricatore continua a ruotare. Nella console viene generato il seguente errore:

```
[ERROR] Page Builder was rendering for 5 seconds without releasing locks.
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
