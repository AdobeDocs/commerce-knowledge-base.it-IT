---
title: "ACSD-51574: immagine non aggiornata sul front-end quando viene sostituita con un’altra immagine"
description: Applica la patch ACSD-51574 per risolvere il problema di Adobe Commerce, se l’immagine non viene aggiornata sul front-end dopo averla sostituita con un’altra immagine.
feature: Configuration
role: Admin
exl-id: a6f26126-71c3-43c2-bba4-60a914d7ec11
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-51574: immagine non aggiornata sul front-end quando viene sostituita con un’altra immagine

La patch ACSD-51574 risolve il problema se l’immagine non viene aggiornata sul front-end dopo essere stata sostituita con un’altra immagine. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.37. L’ID della patch è ACSD-51574. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’immagine non viene aggiornata sul front-end dopo essere stata sostituita con un’altra immagine.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto con alcune immagini.
1. Modifica il prodotto e carica un&#39;immagine con un nome noto (esempio: *image.jpg*).
1. Salva il prodotto.
1. Modifica nuovamente il prodotto ed elimina la versione precedente dell’immagine, quindi carica la nuova versione dell’immagine con lo stesso nome. **Assicurarsi che la nuova versione sia visibilmente diversa per visualizzare il problema.**
1. Salva il prodotto. Sia admin che frontend visualizzano le immagini.
1. Modifica nuovamente il prodotto e carica nuovamente la stessa nuova immagine (utilizzando lo stesso nome).
1. Salva il prodotto e controlla la pagina del prodotto sul front-end.

<u>Risultati previsti</u>:

L’immagine caricata la seconda volta deve essere la nuova immagine, insieme al nome dell’immagine rinominata.

<u>Risultati effettivi</u>:

L’immagine caricata la seconda volta è la versione precedente dell’immagine eliminata in precedenza, invece della stessa nuova immagine.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
