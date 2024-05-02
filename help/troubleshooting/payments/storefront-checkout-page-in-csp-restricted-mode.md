---
title: Risolvere i problemi relativi alla pagina di estrazione della vetrina in [!UICONTROL CSP] modalità con restrizioni
description: Questo articolo spiega gli errori che potrebbero verificarsi durante la visualizzazione della pagina di pagamento in modalità CSP limitata e fornisce soluzioni per correggerli.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Risolvere i problemi relativi alla pagina di estrazione della vetrina in [!UICONTROL CSP] modalità con restrizioni

Questo articolo fornisce spiegazioni e correzioni per i problemi di Adobe Commerce 2.4.7 durante la visualizzazione della pagina di pagamento in **[!UICONTROL CSP restricted mode]**, con &quot;*Si è rifiutato di eseguire lo script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot; nel registro della console del browser.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud, Adobe Commerce on-premise e Magento Open Source:

* 2.4.7.
* 2,4,6-pX
* 2,4,5-pX
* 2,4,4-pX

## Problema - La pagina Storefront Checkout è danneggiata o non è in grado di essere caricata

Il **storefront checkout** la pagina è interrotta o non è in grado di caricarla, con il simbolo &quot;*Si è rifiutato di eseguire lo script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot; nel registro della console del browser.

<u>Passaggi da riprodurre</u>:

1. Vai alla vetrina.
1. Aggiungi un prodotto al carrello e procedi al pagamento.

<u>Risultati previsti</u>:

La pagina di pagamento viene caricata completamente normalmente.

<u>Risultati effettivi</u>:

La pagina di pagamento è vuota o non contiene componenti. I seguenti elementi [!DNL JS] viene visualizzato un errore nel registro della console del browser: &quot;*Si è rifiutato di eseguire lo script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot;

### Causa

In Adobe Commerce e Magento Open Source versione 2.4.7 e successive, **[!UICONTROL CSP]** è configurato in `restrict-mode`, per impostazione predefinita, per le pagine di pagamento nelle aree vetrina e amministrazione e in `report-only` per tutte le altre pagine.
Il corrispondente **[!UICONTROL CSP]** l&#39;intestazione non contiene `unsafe-inline` parola chiave all&#39;interno del `script-src` direttiva per le pagine di pagamento. Inoltre, solo [!DNL whitelisted] gli script in linea sono consentiti.

### Soluzione

Gli utenti potrebbero visualizzare errori del browser a causa di alcuni script bloccati a causa di **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Per risolvere il problema, è necessario:</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) gli script bloccati che utilizzano `SecureHtmlRenderer` classe.
1. Utilizza il `CSPNonceProvider` classe per consentire l&#39;esecuzione di script.
Adobe Commerce e Magento Open Source 2.4.7 e versioni successive includono **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] per facilitare la generazione di [!DNL nonce] stringhe per ogni richiesta. Questi [!DNL nonce] le stringhe vengono quindi collegate al [!UICONTROL CSP] intestazione.

   Utilizza il `generateNonce` funzione in `Magento\Csp\Helper\CspNonceProvider` per ottenere un [!DNL nonce] stringa.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Aggiungi un [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al modulo di `csp_whitelist.xml` file.

## Problema - Il metodo di pagamento è mancante o non funziona

Metodo di pagamento mancante o non funzionante nel **storefront checkout** , con &quot;*Si è rifiutato di eseguire lo script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot; nel registro della console del browser.

<u>Passaggi da riprodurre</u>:

1. Vai alla vetrina.
2. Aggiungi un prodotto al carrello e procedi al pagamento.
3. Seleziona un metodo di pagamento.

<u>Risultati previsti</u>:

Puoi selezionare un metodo di pagamento e procedere con l’ordine.

<u>Risultati effettivi</u>:

Metodo di pagamento mancante o non funzionante. I seguenti elementi [!DNL JS] viene visualizzato un errore nel registro della console del browser: &quot;*Si è rifiutato di eseguire lo script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot;

### Causa

In Adobe Commerce e Magento Open Source versione 2.4.7 e successive, **[!UICONTROL CSP]** è configurato in `restrict-mode`, per impostazione predefinita, per le pagine di pagamento nelle aree vetrina e amministrazione e in `report-only` per tutte le altre pagine.
Il corrispondente **[!UICONTROL CSP]** l&#39;intestazione non contiene `unsafe-inline` parola chiave all&#39;interno del `script-src` direttiva per le pagine di pagamento. Inoltre, solo [!DNL whitelisted] gli script in linea sono consentiti.

### Soluzione

Gli utenti potrebbero visualizzare errori del browser a causa di alcuni script bloccati a causa di **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Per risolvere il problema, è necessario:</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) gli script bloccati che utilizzano `SecureHtmlRenderer` classe.
1. Utilizza il `CSPNonceProvider` classe per consentire l&#39;esecuzione di script.
Adobe Commerce e Magento Open Source 2.4.7 e versioni successive includono **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] per facilitare la generazione di [!DNL nonce] stringhe per ogni richiesta. Questi [!DNL nonce] le stringhe vengono quindi collegate al [!UICONTROL CSP] intestazione.

   Utilizza il `generateNonce` funzione in `Magento\Csp\Helper\CspNonceProvider` per ottenere un [!DNL nonce] stringa.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Aggiungi un [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al modulo di `csp_whitelist.xml` file.

## Problema - Il cliente non può effettuare un ordine

Un cliente non è in grado di effettuare un ordine, con il &quot;*Si è rifiutato di eseguire lo script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot; nel registro della console del browser.

<u>Passaggi da riprodurre</u>:

1. Vai alla vetrina.
2. Aggiungi un prodotto al carrello e procedi al pagamento.
3. Seleziona un metodo di pagamento.
4. Clic **Inserisci ordine**.

<u>Risultati previsti</u>:

Puoi effettuare un ordine con successo.

<u>Risultati effettivi</u>:

Non sei in grado di fare un ordine. I seguenti elementi [!DNL JS] viene visualizzato un errore nel registro della console del browser: &quot;*Si è rifiutato di eseguire lo script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot;

### Causa

In Adobe Commerce e Magento Open Source versione 2.4.7 e successive, **[!UICONTROL CSP]** è configurato in `restrict-mode`, per impostazione predefinita, per le pagine di pagamento nelle aree vetrina e amministrazione e in `report-only` per tutte le altre pagine.
Il corrispondente **[!UICONTROL CSP]** l&#39;intestazione non contiene `unsafe-inline` parola chiave all&#39;interno del `script-src` direttiva per le pagine di pagamento. Inoltre, solo [!DNL whitelisted] gli script in linea sono consentiti.

### Soluzione

Gli utenti potrebbero visualizzare errori del browser a causa di alcuni script bloccati a causa di **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Per risolvere il problema, è necessario:</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) gli script bloccati che utilizzano `SecureHtmlRenderer` classe.
1. Utilizza il `CSPNonceProvider` classe per consentire l&#39;esecuzione di script.
Adobe Commerce e Magento Open Source 2.4.7 e versioni successive includono **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] per facilitare la generazione di [!DNL nonce] stringhe per ogni richiesta. Questi [!DNL nonce] le stringhe vengono quindi collegate al [!UICONTROL CSP] intestazione.

   Utilizza il `generateNonce` funzione in `Magento\Csp\Helper\CspNonceProvider` per ottenere un [!DNL nonce] stringa.

   ```php
   use Magento\Csp\Helper\CspNonceProvider;
   
   class MyClass
   {
   
       /**
        * @var CspNonceProvider
        */
       private $cspNonceProvider;
   
       /**
        * @param CspNonceProvider $cspNonceProvider
        */
       public function __construct(CspNonceProvider $cspNonceProvider)
       {
           $this->cspNonceProvider = $cspNonceProvider
       }
   
       /**
        * Get CSP Nonce
        *
        * @return String
        */
       public function getNonce(): string
       {
           return $this->cspNonceProvider->generateNonce();
       }
   }
   ```

1. [Aggiungi un [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al modulo di `csp_whitelist.xml` file.
