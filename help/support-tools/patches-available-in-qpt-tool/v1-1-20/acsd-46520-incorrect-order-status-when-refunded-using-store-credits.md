---
title: "ACSD-46520: stato ordine errato quando rimborsato utilizzando i crediti del negozio"
description: Questo articolo fornisce una soluzione per il problema in cui gli utenti ottengono uno stato dell'ordine errato quando rimborsati utilizzando i crediti del negozio.
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520: stato ordine errato quando rimborsato utilizzando i crediti del negozio

La patch ACSD-46520 risolve il problema che gli utenti ottengono uno stato di ordine errato quando rimborsati utilizzando i crediti del negozio. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20. L’ID della patch è ACSD-46520. Il problema è stato risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 e 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti ricevono uno stato dell&#39;ordine errato quando vengono rimborsati utilizzando i crediti del negozio.

<u>Passaggi da riprodurre</u>:

1. Crea un account cliente nella vetrina e accedi.
1. Assegna crediti in negozio al cliente dall’amministratore. I crediti del negozio devono coprire l&#39;intero ordine.
1. Effettua un ordine utilizzando i crediti del negozio.
1. Fattura l&#39;ordine.
1. Creare una nota di accredito per rimborsare l&#39;intero importo dell&#39;ordine.
Selezionare la casella di controllo **[!UICONTROL Refund to store credit]**.
1. Controlla lo stato dell’ordine.

<u>Risultati previsti</u>:

Lo stato dell&#39;ordine è *Chiuso*.

<u>Risultati effettivi</u>:

Lo stato dell&#39;ordine è *Completo*, che non è corretto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o [!DNL Magento Open Source] on-premise: [Strumenti per le patch di qualità > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida allo strumento per le patch di qualità.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) nella nostra Knowledge Base di supporto.

Per informazioni sulle altre patch disponibili in QPT, vedere [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida dello strumento Patch di qualità.
