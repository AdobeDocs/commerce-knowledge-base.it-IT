---
title: "ACSD-46815: la distribuzione di contenuti statici non riesce con una strategia compatta"
description: Applica la patch ACSD-46815 per risolvere il problema Adobe Commerce in cui la distribuzione di contenuto statico non riesce quando si utilizza una strategia compatta.
exl-id: e94a0911-5cd9-4866-a027-7ea3239555d3
feature: Deploy, Page Content, SCD
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-46815: l’implementazione di contenuti statici non riesce quando si utilizza una strategia compatta

La patch ACSD-46815 risolve il problema relativo all&#39;errore di distribuzione del contenuto statico quando si utilizza la strategia compatta. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20. L’ID della patch è ACSD-46815. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’implementazione di contenuti statici non riesce se si utilizza una strategia compatta.

<u>Passaggi da riprodurre</u>:

1. Distribuisci il contenuto statico con una strategia compatta eseguendo il seguente comando:

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>Risultati previsti</u>:

La distribuzione del contenuto statico è stata completata senza errori.

<u>Risultati effettivi</u>:

L’implementazione di contenuti statici non riesce con una strategia compatta. Durante il processo di distribuzione si verifica l&#39;errore seguente: *I contenuti di /app/pub/static/adminhtml/Magento/base/default/.Impossibile leggere il file /node_modules/@spectrum-css/vars/dist/spectrum-global.css.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
