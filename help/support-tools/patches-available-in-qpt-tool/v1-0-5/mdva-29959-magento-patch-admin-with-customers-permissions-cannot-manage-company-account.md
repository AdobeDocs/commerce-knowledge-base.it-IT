---
title: '''Patch MDVA-29959: l''amministratore con autorizzazioni "Clienti" non è in grado di gestire l''account società'''
description: La patch MDVA-29959 disponibile nello strumento [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versione 1.0.5 risolve il problema per cui un utente amministratore con restrizioni e tutte le autorizzazioni per l'ACL "Cliente" non può gestire aziende (aggiungere o eliminare un'azienda). Il problema è risolto in B2B per Adobe Commerce 2.3.4.
exl-id: ee246380-d37e-4c24-8435-97ae80088227
feature: Admin Workspace, B2B, Companies, Roles/Permissions
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Patch MDVA-29959: l&#39;amministratore con autorizzazioni &quot;Clienti&quot; non può gestire l&#39;account aziendale

La patch MDVA-29959 disponibile nello strumento [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versione 1.0.5 risolve il problema per cui un utente amministratore con restrizioni e tutte le autorizzazioni per l&#39;ACL &quot;Cliente&quot; non può gestire aziende (aggiungere o eliminare un&#39;azienda). Il problema è risolto in B2B per Adobe Commerce 2.3.4.

## Prodotti e versioni interessati

B2B per Adobe Commerce sull’infrastruttura cloud 2.3.0-2.3.3-p1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore con tutte le autorizzazioni per l’ACL &quot;Cliente&quot; non può gestire aziende (aggiungere o eliminare un’azienda).

<u>Passaggi da riprodurre</u>

1. Nell’amministratore di Commerce, crea un nuovo ruolo di amministratore e assegna un utente a tale ruolo.
1. Assegna solo risorse &quot;cliente&quot; al ruolo.
1. Accedi come utente con questo ruolo.
1. Provare a eliminare un account aziendale.

<u>Risultato previsto:</u>

L&#39;account società è stato eliminato.

<u>Risultato effettivo:</u>

Impossibile eliminare l&#39;account società. Hai ottenuto *Le autorizzazioni necessarie per visualizzare questo contenuto.* messaggio di errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
