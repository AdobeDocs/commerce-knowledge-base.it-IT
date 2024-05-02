---
title: "ACSD-54040: The [!UICONTROL Created] è vuoto nei dettagli dell’ordine quando i moduli B2B sono abilitati"
description: Applicare la patch ACSD-54040 per risolvere il problema Adobe Commerce in cui [!UICONTROL Created] è vuoto nella pagina dei dettagli dell’ordine quando i moduli B2B sono abilitati.
feature: B2B
role: Admin, Developer
exl-id: 5c420b94-43e1-40ac-9482-8a2d42f173d9
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-54040 *[!UICONTROL Created]* è vuoto nei dettagli dell’ordine quando i moduli B2B sono abilitati.

La patch ACSD-54040 risolve il problema in cui *[!UICONTROL Created]* Il campo rimane vuoto nella pagina dei dettagli dell’ordine quando i moduli B2B sono abilitati. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-54040. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p5, 2.4.4-p6, 2.4.5-p4, 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando i moduli B2B sono abilitati, il *[!UICONTROL Created]* rimane vuoto nella pagina dei dettagli dell&#39;ordine.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce con il modulo B2B.
1. Crea un nuovo cliente e effettua un ordine.
1. Vai ai dettagli dell’ordine sul front-end e controlla *[!UICONTROL Created]* campo.

<u>Risultati previsti</u>:

Il *[!UICONTROL Created]* visualizza la data di creazione dell’ordine.

<u>Risultati effettivi</u>:

Il *[!UICONTROL Created]* il campo è vuoto

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
