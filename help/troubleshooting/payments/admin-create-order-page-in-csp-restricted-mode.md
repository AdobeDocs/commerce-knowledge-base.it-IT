---
title: Risolvere i problemi relativi alla creazione della pagina dell'ordine in modalità con restrizioni [!UICONTROL CSP]
description: In questo articolo vengono illustrati gli errori di creazione di un ordine sul lato Amministratore quando è abilitata la modalità con restrizioni CSP e vengono fornite soluzioni per correggere tali errori.
feature: Checkout,Security,Orders,Payments
role: Developer
exl-id: c1a0886a-df1f-418a-9e4d-562b28a0d8b3
source-git-commit: 6d0c4ea9576440d66be3b8053a6e362b8ac0ebcb
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Risolvere i problemi relativi alla creazione della pagina dell&#39;ordine in modalità con restrizioni [!UICONTROL CSP]

Questo articolo fornisce spiegazioni e correzioni per i problemi di Adobe Commerce 2.4.7 durante la creazione di un ordine sul lato Amministratore con **[!UICONTROL CSP restricted mode]** abilitato *2}, con il messaggio di errore &quot;* Rifiutato di eseguire lo script in linea perché viola la seguente direttiva dei criteri sulla sicurezza dei contenuti: &quot;script-src ...*&quot; nel registro della console del browser.*

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud, Adobe Commerce on-premise e Magento Open Source:

* 2.4.7.
* 2,4,6-pX
* 2,4,5-pX
* 2,4,4-pX

## Problema - La pagina **Crea ordine** dell&#39;amministratore è interrotta o non è in grado di essere caricata

La pagina Admin **create order** è interrotta o non è in grado di caricare. &quot;*Impossibile eseguire lo script in linea perché viola la seguente direttiva dei criteri sulla sicurezza dei contenuti: messaggio di errore &quot;script-src ...*&quot; nel registro della console del browser.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Crea un nuovo ordine.

<u>Risultati previsti</u>:

La pagina Admin **create order** viene caricata completamente normalmente.

<u>Risultati effettivi</u>:

La pagina Amministrazione **crea ordine** contiene componenti vuoti o mancanti. Nel registro della console del browser viene visualizzato il seguente errore [!DNL JS]: &quot;*Rifiutata l&#39;esecuzione dello script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot;

### Causa

In Adobe Commerce e Magento Open Source versione 2.4.7 e successive, **[!UICONTROL CSP]** è configurato in `restrict-mode` per impostazione predefinita per le pagine di pagamento nelle aree storefront e admin e in modalità `report-only` per tutte le altre pagine.
L&#39;intestazione **[!UICONTROL CSP]** corrispondente non contiene la parola chiave `unsafe-inline` all&#39;interno della direttiva `script-src` per le pagine di pagamento. Inoltre, sono consentiti solo [!DNL whitelisted] script in linea.

### Soluzione

Gli utenti potrebbero visualizzare errori del browser a causa di alcuni script bloccati a causa di [!UICONTROL CSP]:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

Metodo di pagamento mancante o non funzionante nella pagina di creazione dell&#39;ordine **amministratore**, con il messaggio di errore &quot;*Rifiutato di eseguire lo script in linea perché viola la seguente direttiva dei criteri di sicurezza del contenuto: &quot;script-src ...*&quot; nel registro della console del browser.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Crea un nuovo ordine.
1. Crea un nuovo cliente.
1. Inserire i dettagli del cliente.
1. Inserire i dettagli dell&#39;ordine (prodotti, metodo di spedizione).
1. Seleziona un metodo di pagamento.

<u>Risultati previsti</u>:

Puoi selezionare un metodo di pagamento e procedere con l’ordine.

<u>Risultati effettivi</u>:

Metodo di pagamento mancante o non funzionante. Nel registro della console del browser viene visualizzato il seguente errore [!DNL JS]: &quot;*Rifiutata l&#39;esecuzione dello script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot;.

### Causa

In Adobe Commerce e Magento Open Source versione 2.4.7 e successive, **[!UICONTROL CSP]** è configurato in `restrict-mode` per impostazione predefinita per le pagine di pagamento nelle aree storefront e admin e in modalità `report-only` per tutte le altre pagine.
L&#39;intestazione **[!UICONTROL CSP]** corrispondente non contiene la parola chiave `unsafe-inline` all&#39;interno della direttiva `script-src` per le pagine di pagamento. Inoltre, sono consentiti solo [!DNL whitelisted] script in linea.

### Soluzione

Gli utenti potrebbero visualizzare errori del browser a causa di alcuni script bloccati a causa di **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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

1. [aggiungi a [!DNL hash]](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#using-inline-scripts-and-styles-is-discouraged-in-favor-of-ui-components-and-classes) al file `csp_whitelist.xml` del modulo.

## Problema - L’amministratore non può effettuare un ordine

Un amministratore non può inviare un ordine nella pagina **Crea ordine** dell&#39;amministratore, con il messaggio di errore &quot;*Rifiutato di eseguire lo script in linea perché viola la seguente direttiva dei criteri di sicurezza del contenuto: &quot;script-src ...*&quot; nel registro della console del browser.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Crea un nuovo ordine.
1. Crea un nuovo cliente.
1. Inserire i dettagli del cliente.
1. Inserire i dettagli dell&#39;ordine (prodotti, metodo di spedizione).
1. Seleziona un metodo di pagamento.
1. Invia l’ordine.

<u>Risultati previsti</u>:

Sei in grado di inviare un ordine correttamente.

<u>Risultati effettivi</u>:

Non puoi inviare un ordine. Nel registro della console del browser viene visualizzato il seguente errore [!DNL JS]: &quot;*Rifiutata l&#39;esecuzione dello script in linea perché viola la seguente direttiva del criterio sulla sicurezza dei contenuti: &quot;script-src ...*&quot;

### Causa

In Adobe Commerce e Magento Open Source versione 2.4.7 e successive, **[!UICONTROL CSP]** è configurato in `restrict-mode` per impostazione predefinita per le pagine di pagamento nelle aree storefront e admin e in modalità `report-only` per tutte le altre pagine.
L&#39;intestazione **[!UICONTROL CSP]** corrispondente non contiene la parola chiave `unsafe-inline` all&#39;interno della direttiva `script-src` per le pagine di pagamento. Inoltre, sono consentiti solo [!DNL whitelisted] script in linea.

### Soluzione

Gli utenti potrebbero visualizzare errori del browser a causa di alcuni script bloccati a causa di **[!UICONTROL CSP]**:

`Refused to execute inline script because it violates the following [!UICONTROL Content Security Policy] directive: "script-src`

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
