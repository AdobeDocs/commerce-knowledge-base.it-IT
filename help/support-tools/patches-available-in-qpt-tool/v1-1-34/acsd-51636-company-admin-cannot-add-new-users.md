---
title: "ACSD-51636: l’amministratore dell’azienda non può aggiungere nuovi utenti dalla sezione account cliente"
description: Applica la patch ACSD-51636 per risolvere il problema di Adobe Commerce, per cui l’amministratore dell’azienda non può aggiungere nuovi utenti dalla sezione dell’account cliente nonostante disponga di tutti i ruoli e le autorizzazioni necessari.
feature: Admin Workspace, B2B, Companies, Customer Service
role: Admin
exl-id: 78395584-e5d3-414e-859d-a68ce1af5af1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51636: l’amministratore dell’azienda non può aggiungere nuovi utenti dalla sezione dell’account cliente

La patch ACSD-51636 risolve il problema per cui l’amministratore dell’azienda non può aggiungere nuovi utenti dalla sezione account cliente nonostante disponga di tutti i ruoli e le autorizzazioni necessari. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34. L’ID della patch è ACSD-51636. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’amministratore società non può aggiungere nuovi utenti dalla sezione account cliente nonostante disponga di tutti i ruoli e le autorizzazioni necessari.

Prerequisiti:

* Il modulo B2B è installato.
* La funzionalità aziendale è abilitata.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova società.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifica **[!UICONTROL Company Admin]** digita in *Cliente*.
1. Accedi come cliente.
1. Vai a **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** > **[!UICONTROL Add User]** e aggiungi i dettagli per l’utente e attivalo.
1. Salva il nuovo utente.

<u>Risultati previsti</u>

L’utente amministratore può aggiungere un nuovo utente.

<u>Risultati effettivi</u>

* L’utente amministratore riceve un messaggio di errore: *Si è verificato un errore*.
* L’utente amministratore non può creare un nuovo cliente.
* Il registro contiene il seguente errore:

  ```PHP
      report.CRITICAL: Error: Call to a member function __toArray() on null in app/code/Magento/LoginAsCustomerLogging/Observer/LogSaveCustomerObserver.php:123
  ```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nel [!DNL Quality Patches Tool] guida.
