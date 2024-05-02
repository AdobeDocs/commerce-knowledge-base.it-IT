---
title: "ACSD-51471: l’utente amministratore non può salvare l’aggiornamento pianificato per il prodotto in bundle"
description: Applica la patch ACSD-51471 per risolvere il problema di Adobe Commerce, a causa del quale un utente amministratore non può salvare un aggiornamento pianificato per un prodotto in bundle che utilizza un prodotto semplice con un aggiornamento pianificato.
exl-id: 7d80aef0-8505-4491-bde3-5b1a30b840f6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-51471: l’utente amministratore non può salvare l’aggiornamento pianificato per il prodotto in bundle

La patch ACSD-51471 risolve il problema per cui un utente amministratore non può salvare un aggiornamento pianificato per un prodotto in bundle che utilizza un prodotto semplice con un aggiornamento pianificato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.33. L’ID della patch è ACSD-51471. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti amministratori non possono salvare un aggiornamento pianificato per un prodotto in bundle che utilizza un prodotto semplice con un aggiornamento pianificato.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Aggiungi un aggiornamento pianificato per il prodotto semplice con solo il *Data di inizio* e no *Data di fine*.
1. Dopo aver applicato l’aggiornamento, modifica lo SKU del prodotto.
1. Crea un prodotto in bundle e aggiungi il prodotto semplice creato nel passaggio 1 come prodotto secondario.
1. Crea un aggiornamento pianificato per il prodotto nel pacchetto per abilitare il prodotto nel pacchetto. Fornisci entrambi *Data di inizio* e *Data di fine* per l’aggiornamento pianificato.
1. Salva l’aggiornamento pianificato.

<u>Risultati previsti</u>:

L&#39;aggiornamento pianificato è stato salvato.

<u>Risultati effettivi</u>:

Durante il salvataggio dell’aggiornamento pianificato si verifica il seguente errore: *Il prodotto richiesto non esiste. Verifica il prodotto e riprova.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
