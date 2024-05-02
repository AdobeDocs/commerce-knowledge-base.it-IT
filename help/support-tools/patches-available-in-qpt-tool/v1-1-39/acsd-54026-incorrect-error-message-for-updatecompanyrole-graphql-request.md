---
title: "ACSD-54026: messaggio di errore non corretto per la richiesta GraphQL updateCompanyRole"
description: Applica la patch ACSD-54026 per risolvere il problema Adobe Commerce in presenza di un messaggio di errore non corretto per una richiesta updateCompanyRole GraphQL per un utente non autorizzato.
feature: Roles/Permissions
role: Admin, Developer
exl-id: c18a8815-975a-499d-a372-8635d89aa673
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-54026: messaggio di errore non corretto per `updateCompanyRole` richiesta GraphQL

La patch ACSD-54026 risolve il problema relativo alla presenza di un messaggio di errore non corretto per un `updateCompanyRole` Richiesta GraphQL per un utente non autorizzato. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.39. L’ID della patch è ACSD-54026. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Ricezione di un messaggio di errore non corretto per un `updateCompanyRole` Richiesta GraphQL per un utente non autorizzato.

<u>Passaggi da riprodurre</u>:

1. Abilita l’azienda B2B nella configurazione.
1. Crea una società.
1. Invia un `updateCompanyRole` GraphQL richiede senza passare un token Bearer o con un token Bearer non valido.
1. Osserva il messaggio di errore nella risposta di GraphQL.

<u>Risultati previsti</u>:

Viene visualizzato il seguente messaggio di errore: *Il cliente corrente non è autorizzato.*

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore: *Il cliente non è un utente aziendale.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
