---
title: "MDVA-31150: fattura senza informazioni sul credito dell'archivio"
description: La patch di MDVA-31150 risolve il problema relativo alla creazione di una fattura senza memorizzare le informazioni sul credito. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8. Il problema verrà risolto in Adobe Commerce versione 2.4.2.
exl-id: 70c87b67-6449-4285-9679-cca81613aa72
feature: Invoices, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-31150: fattura senza informazioni sul credito del negozio

La patch di MDVA-31150 risolve il problema relativo alla creazione di una fattura senza memorizzare le informazioni sul credito. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.8. Il problema verrà risolto in Adobe Commerce versione 2.4.2.

## Prodotti e versioni interessati

* Questa patch è stata progettata per Adobe Commerce su infrastruttura cloud 2.3.5-p2.
* La patch è compatibile anche con Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure da 2.3.0 a 2.3.5-p2 e da 2.4.0 a 2.4.0-p1.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Dopo l&#39;ordine di fatturazione tramite API, le informazioni relative al saldo cliente e alla gift card utilizzate non sono presenti nella fattura.

<u>Passaggi da riprodurre</u>

1. Aggiungere un importo a credito del punto vendita a un conto cliente: nella barra laterale Amministratore, vai a **Clienti** > **Tutti i clienti.**
1. Trova il record del cliente e fai clic su **Modifica** nella colonna Azione, quindi **Credito store** > Aggiorna il saldo > **Salva cliente**.
1. Vai a Vetrina e aggiungi i prodotti al carrello.
1. Effettuare un ordine applicando l&#39;importo della carta di credito o della gift card come pagamento parziale.
1. Crea fattura tramite `REST API>POST>/rest/V1/order/1/invoice` con payload:    ```    { "capture": true, "items": [ { "extension_attributes": {}, "order_item_id": 3, "qty": 1 } ], "notify": true, "appendComment": true, "comment": { "extension_attributes": {}, "comment": "string", "is_visible_on_front": 0 }, "arguments": { "extension_attributes": {} }}    ```
1. Ottieni la fattura appena creata utilizzando `REST API>GET>/rest/V1/invoices/1`.

<u>Risultato previsto</u>

Il saldo della carta di credito e regalo del Negozio viene restituito dalla chiamata API.

<u>Risultato effettivo</u>

Il saldo della carta di credito e regalo del Negozio non viene restituito dalla chiamata API.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
