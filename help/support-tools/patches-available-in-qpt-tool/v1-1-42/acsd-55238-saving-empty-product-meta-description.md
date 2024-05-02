---
title: "ACSD-55238: salvataggio della metadescrizione del prodotto vuota"
description: Applica la patch ACSD-55238 per risolvere il problema Adobe Commerce relativo a una descrizione del prodotto contenente il codice HTML generato da [!DNL Page Builder] Nella meta description viene sempre visualizzato un altro editor di HTML e non è possibile impostarlo su vuoto.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 250026c3-925d-4a62-9855-d892c86d3d24
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-55238: salvataggio della metadescrizione del prodotto vuota

La patch ACSD-55238 risolve il problema per cui nella meta description viene sempre visualizzata una descrizione del prodotto contenente codice HTML generato da un editor HTML. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42. L’ID della patch è ACSD-55238. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Descrizione del prodotto contenente il codice HTML generato da [!DNL Page Builder] Nella meta description viene sempre visualizzato un altro editor di HTML e non è possibile impostarlo su vuoto.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** e crea un nuovo blocco con qualsiasi contenuto.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** e creare un nuovo prodotto. Imposta la descrizione meta su vuota.
1. Aggiungi il blocco creato in precedenza utilizzando *[!DNL Page Builder]* nel *[!UICONTROL Content]* e salvare il prodotto.
1. Apri il prodotto nella vetrina e controlla il relativo elemento documento `meta name = "description"`.

<u>Risultati previsti</u>:

La metadescrizione è vuota.

<u>Risultati effettivi</u>:

Quando un prodotto ha un blocco nella sua descrizione, viene utilizzato per la metadescrizione del prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
