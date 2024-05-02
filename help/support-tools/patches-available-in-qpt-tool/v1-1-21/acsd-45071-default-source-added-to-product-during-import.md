---
title: "ACSD-45071: origine predefinita aggiunta al prodotto durante l’importazione"
description: La patch ACSD-45071 risolve il problema relativo all'aggiunta dell'origine predefinita al prodotto durante l'importazione. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 è installato. L’ID della patch è ACSD-45071. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: 8d8dbb06-6133-4d7a-939a-8bf18caec81c
feature: Data Import/Export, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-45071: origine predefinita aggiunta al prodotto durante l&#39;importazione

La patch ACSD-45071 risolve il problema relativo all&#39;aggiunta dell&#39;origine predefinita al prodotto durante l&#39;importazione. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21. L’ID della patch è ACSD-45071. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Dopo l&#39;importazione di un prodotto, l&#39;origine predefinita viene assegnata automaticamente al prodotto, la quantità viene impostata su zero e lo stato viene impostato su esaurito.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova origine.
1. Create un nuovo materiale utilizzando la nuova origine.
1. Nella pagina di modifica del prodotto in Adobe Commerce Admin, assegna solo il materiale promozionale personalizzato, imposta una certa quantità e imposta lo stato del materiale su **[!UICONTROL In Stock]**.
1. Importa il prodotto tramite **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**.

<u>Risultati previsti</u>:

L’origine predefinita non viene assegnata automaticamente al prodotto dopo l’importazione.

<u>Risultati effettivi</u>:

L&#39;origine predefinita viene assegnata al prodotto dopo l&#39;importazione con stato esaurito e quantità zero.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
