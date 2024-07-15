---
title: "MDVA-35982: impossibile spedire alcuni ordini"
description: La patch di MDVA-35982 corregge l'errore quando un utente amministratore limitato a un sito Web specifico non può creare una spedizione per l'ordine effettuato sullo stesso sito Web. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L'ID della patch è MDVA-35982. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: f41c6572-66bb-4697-93e3-da34b81829e2
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# MDVA-35982: impossibile spedire alcuni ordini

La patch di MDVA-35982 corregge l&#39;errore quando un utente amministratore limitato a un sito Web specifico non può creare una spedizione per l&#39;ordine effettuato sullo stesso sito Web. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-35982. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il commerciante non è in grado di spedire alcuni ordini.

<u>Passaggi da riprodurre</u>:

1. Scegli qualsiasi sito web del prodotto ad eccezione del negozio predefinito. Per i passaggi dettagliati, consulta [Prodotto nei siti Web](https://docs.magento.com/user-guide/catalog/settings-basic-websites.html) nella guida utente.
1. Crea un ruolo utente per l’amministratore con ambiti dei ruoli personalizzati, in cui il sito web/store predefinito non è selezionato. Consulta [Definire un ruolo](https://docs.magento.com/user-guide/system/permissions-user-roles.html#define-a-role) nella guida utente per i passaggi dettagliati.
1. Aprire il prodotto in modalità di modifica e impostare un prezzo di gruppo per il prodotto, in **Advanced Pricing**. Consulta [Prezzo di gruppo](https://docs.magento.com/user-guide/catalog/product-price-group.html) nella nostra guida utente per i passaggi dettagliati.
1. Crea un ordine con questo prodotto.
1. Accedi all’amministratore con questo ruolo utente e crea una spedizione. Consulta [Creazione di una spedizione](https://docs.magento.com/user-guide/sales/shipments-create.html) nella guida utente per i passaggi dettagliati.

<u>Risultati previsti</u>:

La spedizione viene creata.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

`"0":"Notice: Undefined offset: XX in \/vendor\/magento\/module-catalog\/Model\/Product\/Attribute\/Backend\/GroupPrice\/AbstractGroupPrice.php on line 290"`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
