---
title: Modifica della password amministratore su Adobe Commerce nell’infrastruttura cloud
description: '![login_panel_s.png](assets/login_panel_s.png)'
exl-id: 1b6e867e-d314-4e7b-be95-d699e6749896
feature: Admin Workspace, Cloud
source-git-commit: 7dc84525aef4d59346bb9bc980a7ed9b7f6612cf
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Modifica della password amministratore su Adobe Commerce nell’infrastruttura cloud

## Metodo 1: Password dimenticata (reimpostazione tramite e-mail)

![login_panel_s.png](assets/login_panel_s.png)

Leggi i passaggi in [Reimposta la sezione della password per l&#39;accesso amministratore](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/admin-signin.html#admin-sign-in) nella guida utente.

Di seguito sono riportate le note di utilizzo critiche.

### Abilita e-mail in uscita

Prima di utilizzare **Password dimenticata** modulo, [abilita e-mail in uscita](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/outgoing-emails.html) utilizzando [Console cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html).

### Controlla la cartella Posta indesiderata

Se non riesci a trovare il messaggio con un collegamento Reimposta password, controlla *Posta indesiderata* cartella. Il nome dell’e-mail è *Conferma reimpostazione password per nome utente amministratore*.

## Metodo 2: aggiunta di un nuovo utente amministratore

Se non è possibile ripristinare o reimpostare la password per l&#39;utente esistente, è possibile creare un nuovo utente amministratore e impostare una password per questo utente. A tale scopo, effettua le seguenti operazioni:

1. Utilizzare [SSH per accedere all’ambiente remoto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html).
1. Esegui il comando seguente: `bin/magento admin:user:create   --admin-user=%user_name% --admin-password=%your_password% --admin-email=%your_email% --admin-firstname=%admin_user_first_name% --admin-lastname=%admin_user_last_name%`
