---
title: "MC-41359 Commerce patch: impostazioni mancanti parametro cookie SameSite"
description: La patch di Commerce MC-41359 risolve il problema con le impostazioni mancanti per i parametri dei cookie SameSite. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L’ID della patch è MC-41359. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.
exl-id: b48faa3f-0d9a-4d65-9abb-1573c6240635
feature: Observability
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# MC-41359 Commerce patch: impostazioni mancanti per il parametro cookie SameSite

La patch di Commerce MC-41359 risolve il problema con le impostazioni mancanti per i parametri dei cookie SameSite. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L’ID della patch è MC-41359. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.4.2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.6-p1, 2.4.2, 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impostazioni mancanti del parametro per cookie SameSite.

<u>Passaggi da riprodurre:</u>

Prerequisiti:

* Apri Chrome e vai su chrome://flags/
* Abilita **SameSite per cookie predefiniti** e **Cookies without SameSite must be secure (Cookie senza SameSite devono essere protetti)**.
* Aprite la finestra di ispezione Chrome.

<u>Scenario 1</u>

1. Abilita PayPal.
1. Vai alla vetrina.
1. Aggiungi un prodotto al carrello.
1. Vai al pagamento.

<u>Scenario 2</u>

Se si dispone di New Relic [abilitato](https://docs.magento.com/user-guide/reports/new-relic-reporting.html) l’avviso viene visualizzato su qualsiasi pagina front-end.

<u>Risultato effettivo:</u>

Messaggio di avviso nella console del browser: *Un cookie associato a una risorsa intersito è stato impostato senza un attributo SameSite.*

<u>Risultato previsto:</u>

&quot;lax&quot; non deve essere aggiunto al dominio del cookie; l’attributo samesite deve essere presente con il valore predefinito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento a [Patch disponibili nello strumento QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
