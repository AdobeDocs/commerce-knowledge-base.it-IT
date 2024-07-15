---
title: Risolvere i problemi relativi alla pagina di estrazione della vetrina in modalità con restrizioni [!UICONTROL CSP]
description: Questo articolo spiega gli errori che potrebbero verificarsi durante la visualizzazione della pagina di pagamento in modalità CSP limitata e fornisce soluzioni per correggerli.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: fb92b75d-c88b-4810-a309-d6ab38485e86
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# Risolvere i problemi relativi alla pagina di estrazione della vetrina in modalità con restrizioni [!UICONTROL CSP]

Questo articolo fornisce spiegazioni e correzioni per i problemi di Adobe Commerce 2.4.7 durante la visualizzazione della pagina di estrazione in **[!UICONTROL CSP restricted mode]**, con il messaggio di errore &quot;*Rifiutato di eseguire lo script in linea perché viola la seguente direttiva Content Security Policy: &quot;script-src ...*&quot; nel registro della console del browser.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud, Adobe Commerce on-premise e Magento Open Source:

* 2.4.7.
* 2,4,6-pX
* 2,4,5-pX
* 2,4,4-pX

## Problema - La pagina Storefront Checkout è danneggiata o non è in grado di essere caricata

La pagina **storefront checkout** è interrotta o non è in grado di essere caricata con &quot;*Rifiutata l&#39;esecuzione dello script in linea perché viola la seguente direttiva dei criteri sulla sicurezza dei contenuti: messaggio di errore &quot;script-src ...*&quot; nel registro della console del browser.

<u>Passaggi da riprodurre</u>:

1. Vai alla vetrina.
1. Aggiungi un prodotto al carrello e procedi al pagamento.

<u>Risultati previsti</u>:

La pagina di pagamento viene caricata completamente normalmente.

<u>Risultati effettivi</u>:

La pagina di pagamento è vuota o non contiene componenti. Nel registro della console del browser viene visualizzato il seguente errore [!DNL JS]: &quot;*Rifiutata l&#39;esecuzione dello script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot;

### Causa

In Adobe Commerce e Magento Open Source versione 2.4.7 e successive, **[!UICONTROL CSP]** è configurato in `restrict-mode` per impostazione predefinita per le pagine di pagamento nelle aree storefront e admin e in modalità `report-only` per tutte le altre pagine.
L&#39;intestazione **[!UICONTROL CSP]** corrispondente non contiene la parola chiave `unsafe-inline` all&#39;interno della direttiva `script-src` per le pagine di pagamento. Inoltre, sono consentiti solo [!DNL whitelisted] script in linea.

### Soluzione

Gli utenti potrebbero visualizzare errori del browser a causa di alcuni script bloccati a causa di **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Per risolvere il problema, è necessario</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) gli script bloccati utilizzando la classe `SecureHtmlRenderer`.
1. Utilizzare la classe `CSPNonceProvider` per consentire l&#39;esecuzione degli script.
Adobe Commerce e Magento Open Source 2.4.7 e versioni successive includono un provider **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] per facilitare la generazione di stringhe [!DNL nonce] univoche per ogni richiesta. Queste stringhe [!DNL nonce] sono quindi collegate all&#39;intestazione [!UICONTROL CSP].

   Utilizzare la funzione `generateNonce` in `Magento\Csp\Helper\CspNonceProvider` per ottenere una stringa [!DNL nonce].

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

1. [Aggiungi a [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al file `csp_whitelist.xml` del modulo.

## Problema - Il metodo di pagamento è mancante o non funziona

Metodo di pagamento mancante o non funzionante nella pagina **storefront checkout** con il messaggio di errore &quot;*Rifiutato di eseguire lo script in linea perché viola la seguente direttiva dei criteri di sicurezza del contenuto: &quot;script-src ...*&quot; nel registro della console del browser.

<u>Passaggi da riprodurre</u>:

1. Vai alla vetrina.
2. Aggiungi un prodotto al carrello e procedi al pagamento.
3. Seleziona un metodo di pagamento.

<u>Risultati previsti</u>:

Puoi selezionare un metodo di pagamento e procedere con l’ordine.

<u>Risultati effettivi</u>:

Metodo di pagamento mancante o non funzionante. Nel registro della console del browser viene visualizzato il seguente errore [!DNL JS]: &quot;*Rifiutata l&#39;esecuzione dello script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot;

### Causa

In Adobe Commerce e Magento Open Source versione 2.4.7 e successive, **[!UICONTROL CSP]** è configurato in `restrict-mode` per impostazione predefinita per le pagine di pagamento nelle aree storefront e admin e in modalità `report-only` per tutte le altre pagine.
L&#39;intestazione **[!UICONTROL CSP]** corrispondente non contiene la parola chiave `unsafe-inline` all&#39;interno della direttiva `script-src` per le pagine di pagamento. Inoltre, sono consentiti solo [!DNL whitelisted] script in linea.

### Soluzione

Gli utenti potrebbero visualizzare errori del browser a causa di alcuni script bloccati a causa di **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Per risolvere il problema, è necessario</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) gli script bloccati utilizzando la classe `SecureHtmlRenderer`.
1. Utilizzare la classe `CSPNonceProvider` per consentire l&#39;esecuzione degli script.
Adobe Commerce e Magento Open Source 2.4.7 e versioni successive includono un provider **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] per facilitare la generazione di stringhe [!DNL nonce] univoche per ogni richiesta. Queste stringhe [!DNL nonce] sono quindi collegate all&#39;intestazione [!UICONTROL CSP].

   Utilizzare la funzione `generateNonce` in `Magento\Csp\Helper\CspNonceProvider` per ottenere una stringa [!DNL nonce].

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

1. [Aggiungi a [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al file `csp_whitelist.xml` del modulo.

## Problema - Il cliente non può effettuare un ordine

Un cliente non è in grado di effettuare un ordine con &quot;*Rifiutato di eseguire lo script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: messaggio di errore &quot;script-src ...*&quot; nel registro della console del browser.

<u>Passaggi da riprodurre</u>:

1. Vai alla vetrina.
2. Aggiungi un prodotto al carrello e procedi al pagamento.
3. Seleziona un metodo di pagamento.
4. Fai clic su **Inserisci ordine**.

<u>Risultati previsti</u>:

Puoi effettuare un ordine con successo.

<u>Risultati effettivi</u>:

Non sei in grado di fare un ordine. Nel registro della console del browser viene visualizzato il seguente errore [!DNL JS]: &quot;*Rifiutata l&#39;esecuzione dello script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot;

### Causa

In Adobe Commerce e Magento Open Source versione 2.4.7 e successive, **[!UICONTROL CSP]** è configurato in `restrict-mode` per impostazione predefinita per le pagine di pagamento nelle aree storefront e admin e in modalità `report-only` per tutte le altre pagine.
L&#39;intestazione **[!UICONTROL CSP]** corrispondente non contiene la parola chiave `unsafe-inline` all&#39;interno della direttiva `script-src` per le pagine di pagamento. Inoltre, sono consentiti solo [!DNL whitelisted] script in linea.

### Soluzione

Gli utenti potrebbero visualizzare errori del browser a causa di alcuni script bloccati a causa di **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`

<u>Per risolvere il problema, è necessario</u>:

1. [[!DNL Whitelist]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#whitelist-an-inline-script-or-style) gli script bloccati utilizzando la classe `SecureHtmlRenderer`.
1. Utilizzare la classe `CSPNonceProvider` per consentire l&#39;esecuzione degli script.
Adobe Commerce e Magento Open Source 2.4.7 e versioni successive includono un provider **[!UICONTROL Content Security Policy (CSP)]** [!DNL nonce] per facilitare la generazione di stringhe [!DNL nonce] univoche per ogni richiesta. Queste stringhe [!DNL nonce] sono quindi collegate all&#39;intestazione [!UICONTROL CSP].

   Utilizzare la funzione `generateNonce` in `Magento\Csp\Helper\CspNonceProvider` per ottenere una stringa [!DNL nonce].

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

1. [Aggiungi a [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al file `csp_whitelist.xml` del modulo.
