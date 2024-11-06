---
title: L'esportazione manuale degli ordini in MOM non riesce. Il pulsante Export Order (Esporta ordine) restituisce un errore HTTP 404
description: In questo articolo viene illustrato come risolvere un problema, in cui se si tenta di esportare un ordine nel Magento Order Management (MOM) facendo clic sul pulsante **Export Order** (Esporta ordine) nella vista dell’ordine di Commerce, l’amministratore restituisce un errore "404 Page Not Found*" (Pagina non trovata).
exl-id: 75741473-7c9a-4418-a56f-de75ac246d27
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# L&#39;esportazione manuale degli ordini in MOM non riesce. Il pulsante Export Order (Esporta ordine) restituisce un errore HTTP 404

In questo articolo viene illustrato come risolvere un problema, in cui se si tenta di esportare un ordine nel Magento Order Management facendo clic sul pulsante **Esporta ordine** nella visualizzazione ordine di Commerce Admin viene restituito un errore &quot; *404 Pagina non trovata* &quot;.

## Prodotti e versioni interessati

* Adobe Commerce 2.2.x, 2.3.x
* Connettore MOM 2.3.0, 2.4.0, 3.2.0, 3.3.0

## Problema

<u>Passaggi da riprodurre:</u>:

1. In Amministrazione Commerce, fare clic su **Vendite > Ordini**.
1. Fai clic sul pulsante **Crea nuovo ordine**.
1. Selezionare un utente, aggiungere uno o più articoli, selezionare i metodi di pagamento e di spedizione, quindi fare clic sul pulsante **Invia ordine**.
1. Fare clic sul pulsante **Esporta ordine** e quindi **OK**.

<u>Risultato previsto</u>:

L&#39;ordine viene inviato a MOM.

<u>Risultato effettivo</u>:

Viene visualizzata la pagina &quot; *404 Error: Page Not Found*&quot; (Errore: pagina non trovata).

## Soluzione

* Aggiornare il connettore MOM alla versione 3.4.0 per Adobe Commerce 2.3.x o il connettore MOM 2.5 per Adobe Commerce 2.2.x.
* Se l&#39;aggiornamento del connettore MOM non è un&#39;opzione, è possibile esportare l&#39;ordine nel Magento Order Management utilizzando il comando CLI:

```bash
$bin/magento oms:orders:sync
```

## Lettura correlata

[Documentazione tecnica del Magento Order Management](https://commerce-docs.github.io/oms-documentation-archive/)
