---
title: "ACSD-58008: la modifica della data di fine come *empty* fa scomparire l’aggiornamento della pianificazione"
description: Applica la patch ACSD-58008 per risolvere il problema di Adobe Commerce, per cui la modifica della data di fine come *empty* fa scomparire l’aggiornamento della pianificazione.
feature: Staging, Page Content
role: Admin, Developer
source-git-commit: 174ed3b35edeb26b09b04bc7d88111a5719e08f8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-58008: modifica della data di fine come *vuoto* fa scomparire l’aggiornamento della pianificazione

La patch ACSD-58008 risolve il problema relativo alla modifica della data di fine come *vuoto* fa scomparire l’aggiornamento della pianificazione. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48. L’ID della patch è ACSD-58008. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Modifica della data di fine come *vuoto* fa scomparire l’aggiornamento della pianificazione

<u>Passaggi da riprodurre</u>:

1. Accedi come [!UICONTROL Admin].
1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** e creare una pagina.
1. Seleziona la pagina creata e fai clic su **[!UICONTROL Schedule New Update]**. *(Spostati nell’angolo in alto a destra della pagina)*.
1. Crea quattro aggiornamenti. *(ad esempio, come incremento di* 2 *minuti)*.
1. Aggiornare il *aggiornamento 2* e modifica l’ora impostandola su una precedente all’ultima *aggiornamento 4*.
1. Salva gli aggiornamenti effettuati.

<u>Risultati previsti</u>:

L’aggiornamento della pianificazione mostra *aggiornamento 3*.

<u>Risultati effettivi</u>:

L’aggiornamento della pianificazione non mostra *aggiornamento 3*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.