---
title: "MDVA-34867: i valori del set di campi condizione per Aggiornamento pianificato non vengono salvati"
description: La patch MDVA-34867 risolve il problema che impedisce il salvataggio del valore della condizione nella nuova pianificazione aggiornata durante la modifica di una regola del prezzo di catalogo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: bf514ccc-bebd-4ed2-868f-28b02b1e253e
feature: Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-34867: i valori del set di campi condizione per Aggiornamento pianificato non vengono salvati

La patch MDVA-34867 risolve il problema che impedisce il salvataggio del valore della condizione nella nuova pianificazione aggiornata durante la modifica di una regola del prezzo di catalogo. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.0-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il valore della condizione in un nuovo aggiornamento della pianificazione non viene salvato durante la modifica di una regola del prezzo di catalogo.

<u>Passaggi da riprodurre</u>:

1. Accedi ad Admin.
1. Crea una **regola catalogo** con **Condizione** = &quot;*La categoria è 1*&quot;.
1. Pianifica un aggiornamento con una data di inizio futura (esempio: domani) e imposta **Condizione** = &quot;*La categoria è 2, 3*&quot;, quindi salva l&#39;aggiornamento.
1. Fai clic su **Visualizza/Modifica** per l&#39;aggiornamento creato in precedenza e controlla i campi delle condizioni.

<u>Risultati previsti</u>:

La **regola catalogo** **Condizione** = &quot;*Categoria è 2, 3*&quot;, come previsto.

<u>Risultati effettivi</u>:

La **regola catalogo** **Condizione** = &quot;*Categoria è 1*&quot;, ovvero l&#39;aggiornamento non è stato salvato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
