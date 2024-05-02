---
title: '"Gli attributi "ACSD-55241: **Used** e **Times Used** visualizzano valori errati per i coupon generati"'
description: Applica la patch ACSD-55241 per risolvere il problema di Adobe Commerce, in cui gli attributi **Used** e **Times Used** visualizzano valori errati per i coupon generati.
feature: Price Rules
role: Admin, Developer
exl-id: cfe0f8af-423a-4e12-a332-053392cbabed
source-git-commit: 5d0b4743fe49d22c099102490f93dc4065ab4413
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-55241 **Utilizzato** e **Tempi utilizzati** gli attributi visualizzano valori errati per i coupon generati

La patch ACSD-55241 risolve il problema in cui **Utilizzato** e **Tempi utilizzati** gli attributi visualizzano valori errati per i coupon generati. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.47. L’ID della patch è ACSD-55241. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

**Utilizzato** e **Tempi utilizzati** gli attributi visualizzano valori errati per i coupon generati.

<u>Passaggi da riprodurre</u>:

1. Crea **[!UICONTROL Cart Price Rules]** da **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** e aggiungi qualsiasi condizione corrispondente durante l’inserimento di un ordine (esempio: subtotale maggiore di *5$*)

* Applica uno sconto.
* Seleziona **[!UICONTROL Auto Coupon]**.
* Genera alcuni Codici coupon da **Gestisci codici coupon**.
* Reindicizza e pulisci la cache.

1. Creare un **[!UICONTROL customer account]** e accedi al front-end.
1. Aggiungi un prodotto con più di *2* quantità nel carrello e applicare una cedola.
1. Fai clic su **[!UICONTROL Check Out with Multiple Addresses]**.
1. Selezionare un indirizzo separato per ciascuna quantità, inserire l&#39;ordine e completare il processo di pagamento.
1. Osserva il totale dell’ordine dall’amministratore e osserva lo sconto applicato.
1. Inserisci un altro ordine con un altro coupon.
1. Esegui il `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` comando per aggiornare l&#39;utilizzo del codice coupon.

<u>Risultati previsti</u>:

Il conteggio corretto deve essere visualizzato nel **Tempo utilizzato** e **Utilizzato** colonne con **Sì** valore per **[!UICONTROL manage coupon]** nel **[!UICONTROL cart price rule]** nell’amministratore.

<u>Risultati effettivi</u>:

Il conteggio dei codici coupon utilizzati non viene aggiornato in **Tempo utilizzato** nella griglia dei coupon e nella colonna **Utilizzato** mostra la colonna *No* valore se si effettua un ordine con più indirizzi di spedizione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
