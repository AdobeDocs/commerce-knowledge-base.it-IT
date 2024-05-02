---
title: "ACSD-56886: il prodotto configurabile esaurisce le scorte quando i prodotti secondari sono disabilitati"
description: Applica la patch ACSD-56886 per risolvere il problema di Adobe Commerce, in cui il prodotto configurabile diventa un elemento figlio esaurito quando i prodotti sono disabilitati.
feature: Products
role: Admin, Developer
exl-id: 809b9829-283f-4e3c-bf27-1944057f944f
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56886: il prodotto configurabile esaurisce quando i prodotti secondari sono disabilitati

La patch ACSD-56886 risolve il problema che causa l&#39;esaurimento del prodotto configurabile quando i prodotti secondari vengono disattivati. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45. L’ID della patch è ACSD-56886. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prodotto configurabile diventa esaurito quando i prodotti secondari sono disabilitati.

<u>Passaggi da riprodurre</u>:

1. Accedi come Amministratore.
1. Imposta tutti gli indicizzatori in **[!UICONTROL Update By Schedule]** modalità.
1. Crea il seguente prodotto configurabile:

   * Nome = *TEST CONFIGURABILE 1*
   * Attributo = *colore*
   * Valori = *rosso* e *nero*
   * Prezzo del **rosso**  prodotto secondario = *$ 100*;
   * Prezzo del prodotto secondario &quot;nero&quot; = *$ 200*.

1. Crea il seguente aggiornamento pianificato per il prodotto configurabile:

   * Data inizio = *3* tra pochi minuti.
   * Data di fine = *5* minuti dopo la data di inizio.
   * Nome prodotto = *TEST CONFIGURABILE 1 modificato*.
   * Disattiva il **rosso** prodotto secondario in **Configurabile** sezione.

1. Attendi la data di inizio.
1. Apri i dettagli del prodotto configurabile su Storefront.

<u>Risultati previsti</u>:

Il prodotto configurabile viene visualizzato come **In magazzino** con **Fino a 200** etichetta.

<u>Risultati effettivi</u>:

Il prodotto configurabile viene visualizzato come **Esaurito**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
