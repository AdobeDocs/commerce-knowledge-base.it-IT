---
title: '"ACSD-57315: nuova transazione creata in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante Recupera'''
description: Applicare la patch ACSD-57315 per risolvere il problema Adobe Commerce relativo alla creazione di una nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante fetch nella schermata visualizza transazione di [!UICONTROL Admin].
feature: Payments
role: Admin, Developer
source-git-commit: b7f85e4fdb7ef4a6328a1a411dac765dd8da083e
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57315: creazione nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante fetch

La patch ACSD-57315 risolve il problema relativo alla creazione di una nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante fetch nella schermata visualizza transazione di [!UICONTROL Admin]. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.48. L’ID della patch è ACSD-57315. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Viene creata una nuova transazione in [!DNL PayPal Payflow Pro] ogni volta che si fa clic sul pulsante fetch nella schermata visualizza transazione di [!UICONTROL Admin].

<u>Passaggi da riprodurre</u>:

1. Configura [!DNL PayPal Payflow Pro].
1. Imposta il metodo di transazione su *[!UICONTROL Sale]*.
1. Effettua un ordine utilizzando *Carta di credito*.
1. Apri la transazione da [!UICONTROL Admin].
1. Fai clic sul pulsante **[!UICONTROL Fetch]** pulsante.
1. Verifica [!DNL PayPal] conto per le transazioni relative all&#39;ordine effettuato.

<u>Risultati previsti</u>:

Non viene creata una nuova transazione di pagamento.

<u>Risultati effettivi</u>:

Viene creata una nuova transazione di pagamento per un ordine già pagato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
