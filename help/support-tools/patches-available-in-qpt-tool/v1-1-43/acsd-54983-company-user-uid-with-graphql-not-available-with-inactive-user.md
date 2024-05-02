---
title: "ACSD-54983: UID utente società con GraphQL non disponibile con utente inattivo"
description: Applica la patch ACSD-54983 per risolvere il problema di Adobe Commerce, se non è possibile ottenere l’UID utente dell’azienda con la richiesta GraphQL quando lo stato utente è impostato su inattivo.
feature: GraphQL
role: Admin, Developer
exl-id: 57e7b9ca-3421-4b50-86b4-abdf1b3d79d1
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-54983: UID utente società con GraphQL non disponibile con utente inattivo

La patch ACSD-54983 risolve il problema quando non è possibile ottenere l’UID utente dell’azienda con la richiesta GraphQL quando lo stato utente è impostato su inattivo. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43. L’ID della patch è ACSD-54983. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile ottenere l’UID dell’utente della società con la richiesta GraphQL quando lo stato dell’utente è impostato su inattivo.

<u>Passaggi da riprodurre</u>:

1. Crea un’azienda con un utente amministratore. Ad esempio, company@test.com.
1. Crea un nuovo cliente.
1. Assegnare il nuovo cliente a una società.
1. Ottieni un **[!UICONTROL company admin token]**.
1. Utilizzo di **[!UICONTROL company admin token]**, recupera la struttura aziendale. Consulta [Restituire la struttura della società](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) nella documentazione per gli sviluppatori.
1. La risposta contiene solo *ATTIVO* clienti con i loro ID.
1. Aggiorna l&#39;utente della società a *INATTIVO*.
1. Recupera di nuovo la struttura aziendale.

<u>Risultati previsti</u>:

È possibile ottenere l’UID utente dell’azienda quando lo stato è impostato su inattivo.

<u>Risultati effettivi</u>:

I clienti inattivi non sono presenti nell&#39;elenco. Impossibile ottenere l’UID utente della società quando lo stato è impostato su inattivo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
