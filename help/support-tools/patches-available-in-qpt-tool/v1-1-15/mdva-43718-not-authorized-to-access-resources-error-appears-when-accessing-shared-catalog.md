---
title: '"MDVA-43718: errore "consumer is not authorized to access resources" (Il consumatore non è autorizzato ad accedere alle risorse) durante l’accesso al catalogo condiviso"'
description: La patch MDVA-43718 risolve il problema per cui il consumer di errore *non è autorizzato ad accedere a %resources.* viene visualizzato quando si accede a un catalogo condiviso da un’integrazione personalizzata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. L'ID della patch è MDVA-43718. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: fa783ed4-906e-4ee6-b82a-cfe6db5ae89e
feature: Catalog Management
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43718: errore &quot;consumer is not authorized to access resources&quot; (Il consumatore non è autorizzato ad accedere alle risorse) durante l’accesso al catalogo condiviso

La patch MDVA-43718 risolve il problema per cui l&#39;utente *non è autorizzato ad accedere a %resources.* viene visualizzato quando si accede a un catalogo condiviso da un&#39;integrazione personalizzata. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. L&#39;ID della patch è MDVA-43718. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Durante l&#39;accesso a un catalogo condiviso da un&#39;integrazione personalizzata viene visualizzato l&#39;errore seguente: *Il consumatore non è autorizzato ad accedere a %resources*.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova integrazione da Admin > **System** > **Integration** > **Add Integration**.
1. Aggiungi l’accesso alle seguenti risorse e attiva l’integrazione:

   * Magento_SharedCatalog::list
   * Magento_SharedCatalog::gestisci
   * Magento_Catalog::catalogo

1. Utilizzo dell&#39;accesso all&#39;integrazione: `rest/default/V1/sharedCatalog/1`

<u>Risultati previsti</u>:

Vengono restituiti i dettagli del catalogo condiviso.

<u>Risultati effettivi</u>:

Viene restituito il seguente errore:

```JSON
"message": "The consumer isn't authorized to access %resources.",
"resources": "Magento_SharedCatalog::sharedCatalog"
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
