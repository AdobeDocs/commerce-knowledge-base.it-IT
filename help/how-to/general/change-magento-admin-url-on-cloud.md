---
title: Modificare l’URL amministratore su Adobe Commerce nell’infrastruttura cloud
description: Per impostazione predefinita, l'URL [Commerce Admin](https://experienceleague.adobe.com/it/docs/commerce-admin/start/admin/admin) è impostato su *&lt;domain_name&gt;/admin*. Questo articolo mostra come modificare l’URL.
exl-id: 6236370c-e0a2-45a6-a38f-12e219c540af
feature: Admin Workspace, Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Modificare l’URL amministratore su Adobe Commerce nell’infrastruttura cloud

Per impostazione predefinita, l&#39;URL [Commerce Admin](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin.html?lang=it) è impostato su *&lt;dominio\_name>/admin*. Questo articolo mostra come modificare l’URL.

## Metodo 1: modificare con l’amministratore

Leggi i passaggi: [Utilizzo di un URL amministratore personalizzato > Modifica dall&#39;amministratore](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=it#use-a-custom-admin-url) nella nostra guida utente.

## Metodo 2: Aggiungi variabile di ambiente ADMIN\_URL

### Ambiente di integrazione

Dalla [console cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=it), aggiungi una nuova variabile con:

**Nome:** ADMIN\_URL **Valore:** nuovo URL amministratore

* Per i passaggi dettagliati, consulta [aggiungere variabili di ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=it#configure-environment) nella documentazione per gli sviluppatori.
* Consulta anche [variabili di ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=it) nella documentazione per gli sviluppatori.

### Quando Staging e Produzione non sono disponibili nella console cloud

[Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) richiedendo di aggiungere la variabile ADMIN\_URL per l&#39;ambiente di staging o produzione.

Se l&#39;ambiente di staging e produzione è accessibile dalla console cloud, aggiungere la variabile di ambiente come descritto nella sezione *Ambiente di integrazione* precedente.

### Aggiungere variabili utilizzando Cloud CLI

Puoi aggiungere la variabile ADMIN\_URL utilizzando il seguente comando Cloud CLI (per main):

`magento-cloud variable:update ADMIN_URL --value newAdmin_A8v10 -e master --inheritable false`

Per istruzioni più dettagliate, consulta [Modificare l&#39;URL amministratore](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html?lang=it#change-the-admin-url) nell&#39;argomento Variabili amministratore nella Guida all&#39;infrastruttura di Commerce su Cloud.

L&#39;utilizzo di Cloud CLI per modificare la variabile ADMIN\_URL attiva una ridistribuzione dell&#39;ambiente. Le variabili sono ereditabili per impostazione predefinita; per evitare l’ereditarietà, utilizza le opzioni del comando Cloud CLI per indicare che non desideri che il valore della variabile venga ereditato dagli ambienti figlio. Consulta l&#39;argomento [Visibilità](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html?lang=it#visibility) in Livelli variabili nella Guida all&#39;infrastruttura cloud di Commerce.
