---
title: "ACSD-48164: l’amministratore con restrizioni non può salvare il valore a livello di sito web"
description: Applica la patch ACSD-48164 per risolvere il problema di Adobe Commerce, a causa del quale un amministratore con restrizioni non può salvare un valore a livello di sito web.
exl-id: 6ec15163-ad30-4566-a46c-5756bfd9f8d4
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48164: l’amministratore con restrizioni non può salvare un valore a livello di sito web

La patch ACSD-48164 risolve il problema che impediva a un amministratore con restrizioni di salvare un valore a livello di sito web. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-48164. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’amministratore con restrizioni non è in grado di salvare un valore a livello di sito web.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo sito Web, store e visualizzazione store in [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Creare un nuovo ruolo di amministratore in [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Vai a **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, seleziona il nuovo sito web e assegna questo ruolo a qualsiasi utente amministratore.

1. Seleziona un prodotto e assegna solo il nuovo sito web. Non selezionare il sito Web predefinito.
1. Accedi come utente amministratore assegnato al passaggio due e modifica il prodotto in **[!UICONTROL All Store View]** ambito modificando qualsiasi attributo a livello di sito web come *[!UICONTROL Status]*, *[!UICONTROL Tax Class]* e imposta il prodotto come nuovo.
1. Salva il prodotto.

<u>Risultati previsti</u>:

L’utente amministratore associato all’ambito del ruolo a un sito web può salvare gli attributi del prodotto a livello di sito web utilizzando *[!UICONTROL All Store View]* ambito.

<u>Risultati effettivi</u>:

Viene visualizzato il messaggio di operazione riuscita del salvataggio del prodotto, ma i valori degli attributi del prodotto rimangono invariati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
