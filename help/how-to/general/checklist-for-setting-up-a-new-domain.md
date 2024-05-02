---
title: Elenco di controllo per la configurazione di un nuovo [!DNL domain]
description: Questo è un elenco di controllo per la configurazione di un nuovo [!DNL domain] in Adobe Commerce su infrastruttura cloud.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: cc3dc1e3f9c8f98370ce5db125b402d4c1dfbd6f
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# Elenco di controllo per la configurazione di un nuovo [!DNL domain]

Questo è un elenco di controllo per la configurazione di un nuovo [!DNL domain] in Adobe Commerce su infrastruttura cloud. Si applica indipendentemente dal fatto che si stia semplicemente aggiungendo un nuovo dominio o sostituendo il dominio corrente con uno nuovo.

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud, [tutte le versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Come impostare un nuovo dominio

### Passaggio 1: indica se si tratta di [!DNL Integration, Staging], o [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] non sono supportati. È necessario utilizzare questo metodo: [Configurazione di più siti Web o store: Configura installazione locale](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) nella guida utente.
* **[!DNL Staging]**: vai a **Passaggio 2**.
* **[!DNL Production]**: vai a **Passaggio 3**.

### Passaggio 2 - [!DNL Staging environment]: accedi a [!DNL Pro] o [!DNL Starter]?

* **[!DNL Pro]**: **Inviare una richiesta** per aggiungere il dominio a [!DNL Fastly, Nginx], e configurare [!DNL SSL certificate] (nonché [!DNL Sendgrid domain], se necessario). Una volta configurato, [aggiorna il [!DNL DNS] configurazione con [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>È possibile aggiungere il nuovo [!DNL domain] a [!DNL Fastly] aggiornando la configurazione in [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** come in [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) nella guida utente.

* **[!DNL Starter]**: [!DNL Custom domains] non sono supportati.

### Passaggio 3 - [!DNL Production environment]: accedi a [!DNL Pro] o [!DNL Starter]?

* **[!DNL Pro]**: **Inviare una richiesta** per aggiungere il dominio a [!DNL Fastly, Nginx], e configurare [!DNL SSL certificate] (come [!DNL Sendgrid domain], se necessario). Una volta configurato, continua con **Passaggio 4**.

>[!NOTE]
>
>È possibile aggiungere il nuovo [!DNL domain] a [!DNL Fastly] aggiornando la configurazione in [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html#manage-domains) nella guida utente.

* **[!DNL Starter]**: aggiungi [!DNL domain] al progetto in **[!DNL Domains]** , quindi **invia una richiesta** per fornire **[!DNL ACME Challenge Key]** per [!DNL SSL certificate].

### Passaggio 4: indica se [!DNL domain] vivo?

* **SÌ**: [Aggiornare il [!DNL DNS] configurazione con [!UICONTROL production] impostazioni](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html#update-dns-configuration-with-production-settings).
* **NO**: [Aggiornare il [!DNL DNS] configurazione con [!UICONTROL development] impostazioni](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#update-dns-configuration-with-development-settings).

## Lettura correlata

* [Configurazione di più siti Web o store: Aggiungi nuovo [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html#add-new-domains) nella guida utente.
