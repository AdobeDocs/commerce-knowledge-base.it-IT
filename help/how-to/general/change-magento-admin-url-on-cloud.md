---
title: Modificare l’URL amministratore su Adobe Commerce nell’infrastruttura cloud
description: Per impostazione predefinita, l'URL [Commerce Admin](https://docs.magento.com/m2/ee/user_guide/stores/admin.html) è impostato su *&lt;domain\_name&gt;/admin*. Questo articolo mostra come modificare l’URL.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 04dba4e2adeaaa7649b817444024bf96e7830ad3
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Modificare l’URL amministratore su Adobe Commerce nell’infrastruttura cloud

Per impostazione predefinita, il [Amministratore Commerce](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html) URL impostato su *&lt;domain _name=&quot;&quot;>/admin*. Questo articolo mostra come modificare l’URL.

## Metodo 1: modificare con l’amministratore

Leggi i passaggi: [Utilizzo di un URL amministratore personalizzato > Modifica dall’amministratore](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) nella guida utente.

## Metodo 2: Aggiungi variabile di ambiente ADMIN\_URL

### Ambiente di integrazione

Dalla sezione [Console cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html), aggiungi una nuova variabile con:

**Nome:** ADMIN\_URL **Valore:** nuovo URL amministratore

* Per i passaggi dettagliati, consulta [aggiungere variabili di ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-environment) nella documentazione per gli sviluppatori.
* Consulta anche [variabili di ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html) nella documentazione per gli sviluppatori.

### Quando Staging e Produzione non sono disponibili nella console cloud

[Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) richiesta di aggiunta della variabile ADMIN\_URL per l&#39;ambiente di staging o produzione.

Se Staging e Produzione sono accessibili dalla console Cloud, aggiungi la variabile di ambiente come descritto in *Ambiente di integrazione* sopra.

### Aggiungere variabili utilizzando Cloud CLI

Puoi aggiungere la variabile ADMIN\_URL utilizzando il seguente comando Cloud CLI (per main):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Per istruzioni più dettagliate, consulta [Modificare l’URL dell’amministratore](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=en#change-the-admin-url) nell’argomento Admin variables nella Guida di Commerce su Cloud Infrastructure.

L&#39;utilizzo di Cloud CLI per modificare la variabile ADMIN\_URL attiva una ridistribuzione dell&#39;ambiente. Le variabili sono ereditabili per impostazione predefinita; per evitare l’ereditarietà, utilizza le opzioni del comando Cloud CLI per indicare che non desideri che il valore della variabile venga ereditato dagli ambienti figlio. Consulta la sezione [Visibilità](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) argomento in Livelli variabili nella Guida di Commerce sull’infrastruttura cloud.
