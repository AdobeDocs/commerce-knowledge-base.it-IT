---
title: Elenco di controllo per la configurazione di un nuovo [!DNL domain]
description: Elenco di controllo per la configurazione di un nuovo [!DNL domain] in Adobe Commerce su un'infrastruttura cloud.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 625ed2c7ab79f7bca9a979903e97c44c875e607c
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Elenco di controllo per la configurazione di un nuovo [!DNL domain]

Elenco di controllo per la configurazione di un nuovo [!DNL domain] in Adobe Commerce su infrastruttura cloud. Si applica indipendentemente dal fatto che si stia semplicemente aggiungendo un nuovo dominio o sostituendo il dominio corrente con uno nuovo.

## Prodotti e versioni interessati

Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Come impostare un nuovo dominio

### Passaggio 1: si tratta di [!DNL Integration, Staging] o [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] non sono supportati. È necessario utilizzare questo metodo: [Configurare più siti Web o store: Configurare l&#39;installazione locale](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) nella guida utente.
* **[!DNL Staging]**: Passare al **passaggio 2**.
* **[!DNL Production]**: Passare a **Passaggio 3**.

### Passaggio 2 - [!DNL Staging environment]: si utilizza [!DNL Pro] o [!DNL Starter]?

* **[!DNL Pro]**: **Invia una richiesta** per aggiungere il dominio a [!DNL Fastly, Nginx] e configurare [!DNL SSL certificate] (nonché [!DNL Sendgrid domain], se necessario). Una volta configurata, [aggiorna la [!DNL DNS] configurazione con [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>È possibile aggiungere il nuovo [!DNL domain] a [!DNL Fastly] da solo aggiornando la configurazione in [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** come in [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) nella guida utente.
>
>Se non riesci ad aggiungere il dominio, la causa potrebbe essere uno dei seguenti:
>
>1. Stai eseguendo la migrazione del dominio all&#39;ambiente cloud configurato nel tuo servizio [!DNL Fastly]. In questo caso, invia una richiesta e richiede la delega del dominio.
>1. Si sta eseguendo la migrazione del dominio da Starter a Pro. In tal caso, presentare una domanda di assistenza supplementare.

* **[!DNL Starter]**: [!DNL Custom domains] non sono supportati nell&#39;ambiente di staging.

### Passaggio 3 - [!DNL Production environment]: si utilizza [!DNL Pro] o [!DNL Starter]?

* **[!DNL Pro]**: **Invia una richiesta** per aggiungere il dominio a [!DNL Fastly, Nginx] e configurare [!DNL SSL certificate] (come [!DNL Sendgrid domain], se necessario). Una volta configurato, continuare con il **Passaggio 4**.

>[!NOTE]
>
>È possibile aggiungere il nuovo [!DNL domain] a [!DNL Fastly] da solo aggiornando la configurazione in [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) nella guida utente.
>
>
>Se non riesci ad aggiungere il dominio, la causa potrebbe essere uno dei seguenti:
>
>1. Si sta eseguendo la migrazione del dominio dall&#39;ambiente locale all&#39;ambiente cloud, configurato nel servizio [!DNL Fastly]. In questo caso, invia una richiesta e richiede la delega del dominio.
>1. Si sta eseguendo la migrazione del dominio da Starter a Pro. In tal caso, presentare una domanda di assistenza supplementare.

* **[!DNL Starter]**: Aggiungi [!DNL domain] al progetto nella scheda **[!DNL Domains]**, quindi **invia una richiesta** per fornire **[!DNL ACME Challenge Key]** per [!DNL SSL certificate].

### Passaggio 4: [!DNL domain] è attivo?

* **SÌ**: [Aggiorna la configurazione [!DNL DNS] con [!UICONTROL production] impostazioni](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NO**: [Aggiorna la  [!DNL DNS] configurazione con [!UICONTROL development] impostazioni](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Lettura correlata

* [Configura più siti Web o store: Aggiungi nuovo [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) nella nostra guida utente.
