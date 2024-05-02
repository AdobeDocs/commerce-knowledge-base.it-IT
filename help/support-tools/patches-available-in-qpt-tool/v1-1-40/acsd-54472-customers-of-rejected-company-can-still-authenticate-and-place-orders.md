---
title: "ACSD-54472: i clienti di un’azienda rifiutata possono ancora eseguire l’autenticazione"
description: Applicare la patch ACSD-54472 per risolvere il problema di Adobe Commerce, in cui i clienti di una società rifiutata possono ancora autenticarsi e i clienti di una società bloccata e rifiutata possono ancora effettuare ordini.
feature: B2B
role: Admin, Developer
exl-id: 76fc4553-02b1-4563-91a9-0cda99fa4c7d
source-git-commit: f12e25ac5dd607cc614dd99c90c5e104b2cee6a8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-54472: i clienti di un’azienda rifiutata possono ancora eseguire l’autenticazione

La patch ACSD-54472 risolve il problema per cui i clienti di una società rifiutata possono ancora autenticarsi e i clienti di una società bloccata o rifiutata possono ancora effettuare ordini. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-54472. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I clienti di una società rifiutata possono ancora autenticarsi e i clienti di una società bloccata o rifiutata possono ancora effettuare ordini.

<u>Passaggi da riprodurre</u>:

1. Crea una società.
1. Aggiungi prodotti al carrello tramite [!DNL GraphQL].
1. Modifica lo stato dell’azienda in *Bloccato*.
1. Invia un [!DNL GraphQL] richiesta di effettuare l&#39;ordine e di creare un preventivo negoziabile.
1. Modifica lo stato dell’azienda in *Rifiutato*.
1. Invia un [!DNL GraphQL] per ottenere il token di autorizzazione utente della società.
1. Imposta stato cliente su *Inattivo*.
1. Invia un [!DNL GraphQL] per ottenere il token di autorizzazione utente della società.

<u>Risultati previsti</u>:

* L&#39;ordine e l&#39;offerta negoziabile non vengono inseriti dall&#39;utente del *Bloccato* società.
* Token di autorizzazione non ottenuto per l’utente di *Rifiutato* società.
* Token di autorizzazione non ottenuto per *Inattivo* cliente.

<u>Risultati effettivi</u>:

* L&#39;ordine e il preventivo negoziabile vengono inseriti dall&#39;utente del *Bloccato* società.
* Token di autorizzazione ottenuto per l’utente di *Rifiutato* società.
* Token di autorizzazione ottenuto per *Inattivo* cliente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
