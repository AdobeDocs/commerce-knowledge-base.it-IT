---
title: "ACSD-46618: il widget elenco prodotti mostra prezzi memorizzati nella cache non corretti per il cliente connesso"
description: Applica una patch per risolvere il problema di Adobe Commerce, in cui il widget dell’elenco dei prodotti mostra prezzi memorizzati nella cache non corretti per un cliente connesso.
exl-id: 8b182822-1d3d-4793-871b-cdf4565d0712
feature: Cache, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# ACSD-46618: il widget elenco prodotti mostra prezzi memorizzati nella cache non corretti per un cliente connesso

La patch ACSD-46618 risolve il problema relativo alla visualizzazione di prezzi non corretti nella cache da parte del widget elenco prodotti per un cliente connesso. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21. L’ID della patch è ACSD-46618. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La patch ACSD-46618 risolve il problema relativo alla visualizzazione di prezzi non corretti nella cache da parte del widget elenco prodotti per un cliente connesso.

<u>Passaggi da riprodurre</u>:

1. In Adobe Commerce Admin, seleziona **[!UICONTROL Stores]**, quindi **[!UICONTROL Configuration]**, espandi **[!UICONTROL Sales]**, e seleziona **[!UICONTROL Tax]**. Aggiornare le impostazioni relative alle imposte per visualizzare i prezzi, incluse e escluse le imposte.
1. Imposta **[!UICONTROL Enable Cross Border Trade]** = _Sì_.
1. Creare una regola fiscale applicabile solo agli Stati Uniti.
1. Aggiungi un widget alla home page che include più di un prodotto.
1. Crea due clienti con un indirizzo USA e un indirizzo non USA.
1. Accedi utilizzando il cliente americano dalla vetrina. Assicurati che la pagina sia memorizzata in cache.
1. Osserva il prezzo visualizzato nel widget della pagina principale.
1. Esci e accedi utilizzando il cliente non statunitense.

<u>Risultati previsti</u>:

Il prezzo visualizzato nel widget della home page corrisponde all&#39;indirizzo del cliente.

<u>Risultati effettivi</u>:

Il widget della pagina Home mostra i prezzi utilizzando l’imposta per i clienti non statunitensi.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
