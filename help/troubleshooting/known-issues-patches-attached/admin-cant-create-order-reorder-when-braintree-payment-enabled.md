---
title: L'amministratore non può creare un ordine o riordinarlo quando è abilitato il pagamento Braintree
description: Questo articolo fornisce una patch per il problema di Adobe Commerce 2.4.5 in cui un utente amministratore non può creare ordini o riordini per i clienti quando il metodo di pagamento Braintree è abilitato.
exl-id: 8840aecb-21d9-4965-8c09-395e2d263aaa
feature: Admin Workspace, Native Luma Frontend Development, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# L&#39;amministratore non può creare un ordine o riordinarlo quando è abilitato il pagamento Braintree

Questo articolo fornisce una patch per il problema di Adobe Commerce 2.4.5 in cui un utente amministratore non può creare ordini o riordini per i clienti quando il metodo di pagamento Braintree è abilitato.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.4.5
* Adobe Commerce on-premise 2.4.5
* Magento Open Source 2.4.5

## Problema

<u>Passaggi da riprodurre</u>:

1. Viene utilizzata l&#39;integrazione Braintree di base (**Archivi** > **Configurazioni** > **Vendite** > **Metodo di pagamento** > **Braintree**).
1. Utilizzando Luma Storefront, effettua un ordine.
1. Vai a Interfaccia utente amministratore > **Vendite**.
1. Prova a creare un nuovo ordine per un cliente oppure accedi a un ordine precedentemente inoltrato e fai clic su **Riordina**.

<u>Risultato previsto</u>:

Gli utenti amministratori possono creare con successo ordini e riordini per i clienti quando è abilitato il metodo di pagamento Braintree.

<u>Risultato effettivo</u>:

Gli utenti amministratori non possono creare ordini né riordini per i clienti quando il metodo di pagamento Braintree è abilitato e restituiscono il seguente errore:

```bash
report.CRITICAL: Error: Call to a member function getMethodInstance() on null in /app/vendor/paypal/module-braintree-core/Block/Form.php:174
```

## Causa

Dipendenze di classe non corrette (`vendor/paypal/module-braintree-core/Block/Form.php`)

## Soluzione

Applichi la patch fornita in questo articolo.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, fai clic sul seguente collegamento:

[BUNDLE-3137-composer.patch.zip](assets/BUNDLE-3137-composer.patch.zip)

>[!NOTE]
>
>Inoltre, per Adobe Commerce sui commercianti di infrastrutture cloud: Adobe ha incluso la correzione nella versione 1.0.18 delle patch cloud per Commerce. Per istruzioni sull&#39;applicazione del pacchetto più recente, consulta le [note sulla versione delle patch cloud per Commerce](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html) nella documentazione per gli sviluppatori.

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.4.5
* Adobe Commerce on-premise 2.4.5
* Magento Open Source 2.4.5

>[!NOTE]
>
>La patch non è compatibile con altre versioni ed edizioni di Adobe Commerce e di Magento Open Source.

## Come applicare il cerotto

Per istruzioni, consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.
