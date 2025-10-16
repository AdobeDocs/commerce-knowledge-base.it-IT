---
title: Elenco di controllo per la configurazione di un nuovo [!DNL domain]
description: Elenco di controllo per la configurazione di un nuovo [!DNL domain] in Adobe Commerce su un'infrastruttura cloud.
exl-id: bfe0582d-2c6d-4814-908f-dfd8c898bef7
feature: Cache
source-git-commit: 552a290b50f9e0c5fa740f26092c57bac447fe68
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# Elenco di controllo per la configurazione di un nuovo [!DNL domain]

Questo elenco di controllo spiega come impostare un nuovo [!DNL domain] in Adobe Commerce sull&#39;infrastruttura cloud. Si applica sia quando si aggiunge un nuovo dominio che quando si sostituisce quello corrente. Si applica anche dopo aver ottenuto un nuovo ambiente di staging (vedi Passaggio 4).

## Prodotti e versioni interessati

Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Come impostare un nuovo dominio

>[!NOTE]
>
>Prima di procedere con la configurazione del dominio, assicurati che:
>
>Tutti gli URL di base sono configurati per utilizzare HTTPS in **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**, con ambito nella visualizzazione corretta del sito Web o dello store.
>&#x200B;> [Force TLS](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/how-to/redirect-http-to-https-for-all-pages-on-cloud-force-tls#token_type=bearer&expires_in=10799996) is enabled to redirect all HTTP traffic to HTTPS in your Adobe Commerce site on cloud infrastructure (Forza TLS è abilitato per reindirizzare tutto il traffico HTTP a HTTPS nel sito di nell&#39;infrastruttura cloud).

### Passaggio 1: si tratta di [!DNL Integration, Staging] o [!DNL Production environment]?

* **[!DNL Integration]**: [!DNL Custom domains] non sono supportati. È necessario utilizzare questo metodo: [Configurare più siti Web o store: Configurare l&#39;installazione locale](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=it#add-new-domains) nella guida utente.
* **[!DNL Staging]**: Passare al **passaggio 2**.
* **[!DNL Production]**: Passare a **Passaggio 3**.

### Passaggio 2 - [!DNL Staging environment]: si utilizza [!DNL Pro] o [!DNL Starter]?

* **[!DNL Pro]**: **Invia una richiesta** per aggiungere il dominio a [!DNL Fastly, Nginx] e configurare [!DNL SSL certificate] (nonché [!DNL Sendgrid domain], se necessario). Una volta configurata, [aggiorna la [!DNL DNS] configurazione con [!DNL development settings]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=it#update-dns-configuration-with-development-settings).

>[!NOTE]
>
>Per l’architettura PRO, l’aggiunta di un nuovo dominio richiede l’invio di una richiesta di supporto ad Adobe Commerce. Anche se alcuni clienti possono essere in grado di configurare manualmente Fastly tramite Admin Console, questo si applica solo in casi limitati, come quando il dominio non è legato a un altro servizio o progetto Fastly. Tuttavia, la configurazione Nginx è sempre richiesta e questo passaggio deve essere gestito da Adobe. Per questo motivo, l&#39;approccio consigliato e più affidabile consiste nell&#39;inviare un [ticket di supporto](https://experienceleague.adobe.com/home?lang=it&support-tab=home#support) e consentire ad Adobe di gestire l&#39;intero processo di configurazione del dominio.


* **[!DNL Starter]**: [!DNL Custom domains] non sono supportati nell&#39;ambiente di staging.

### Passaggio 3 - [!DNL Production environment]: si utilizza [!DNL Pro] o [!DNL Starter]?

* **[!DNL Pro]**: **Invia una richiesta** per aggiungere il dominio a [!DNL Fastly, Nginx] e configurare [!DNL SSL certificate] (come [!DNL Sendgrid domain], se necessario). Una volta configurato, continuare con il **Passaggio 4**.

>[!NOTE]
>
>È possibile aggiungere il nuovo [!DNL domain] a [!DNL Fastly] da solo aggiornando la configurazione in [!DNL Admin] in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!DNL Fastly Configuration]** > **[!UICONTROL Domains]** [[!DNL Manage domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration.html?lang=it#manage-domains) nella guida utente.
>
>
>Se non riesci ad aggiungere il dominio, la causa potrebbe essere uno dei seguenti:
>
>1. Si sta eseguendo la migrazione del dominio dall&#39;ambiente locale all&#39;ambiente cloud, configurato nel servizio [!DNL Fastly]. In questo caso, invia una richiesta e richiede la delega del dominio.
>1. Si sta eseguendo la migrazione del dominio da Starter a Pro. In tal caso, presentare una domanda di assistenza supplementare.

* **[!DNL Starter]**: Aggiungi [!DNL domain] al progetto nella scheda **[!DNL Domains]**, quindi **invia una richiesta** per fornire **[!DNL ACME Challenge Key]** per [!DNL SSL certificate].

### Passaggio 4: [!DNL domain] è attivo?

* **SÌ**: [Aggiorna la configurazione [!DNL DNS] con [!UICONTROL production] impostazioni](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=it#update-dns-configuration-with-production-settings).
* **NO**: [Aggiorna la  [!DNL DNS] configurazione con [!UICONTROL development] impostazioni](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=it#update-dns-configuration-with-development-settings).

### Passaggio 5: i reindirizzamenti di dominio sono configurati in `magento-vars.php`?

Dopo aver configurato il dominio, è necessario [modificare le variabili](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure-store/multiple-sites#modify-variables) nel file `magento-vars.php` per indirizzare il dominio all&#39;URL del sito Web o dello store appropriato.

### Passaggio 6: la configurazione di [!DNL domain] è verificata?

Se sono stati aggiunti nuovi store, gruppi di store e siti Web in **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** per i nuovi domini, verificare se nel file `app/etc/config.php` vengono visualizzate le sezioni seguenti, ad esempio:

```php
'scopes' => [
    'websites' => [
        'admin' => [
            'website_id' => '0',
            'code' => 'admin',
            'name' => 'Admin',
            'sort_order' => '0',
            'default_group_id' => '0',
            'is_default' => '0',
        ],
        'base' => [
            'website_id' => '1',
            'code' => 'base',
            'name' => 'Main Website',
            'sort_order' => '0',
            'default_group_id' => '1',
            'is_default' => '1',
        ],
        'site2' => [
            'website_id' => '2',
            'code' => 'site2',
            'name' => 'Second Website',
            'sort_order' => '0',
            'default_group_id' => '2',
            'is_default' => '0',
        ],
    ],
    'groups' => [
        0 => [
            'group_id' => '0',
            'website_id' => '0',
            'name' => 'Default',
            'root_category_id' => '0',
            'default_store_id' => '0',
            'code' => 'default',
        ],
        1 => [
            'group_id' => '1',
            'website_id' => '1',
            'name' => 'Main Website Store',
            'root_category_id' => '2',
            'default_store_id' => '1',
            'code' => 'main_website_store',
        ],
        2 => [
            'group_id' => '2',
            'website_id' => '2',
            'name' => 'Second Website Store',
            'root_category_id' => '2',
            'default_store_id' => '2',
            'code' => 'site2store',
        ],
    ],
    'stores' => [
        'admin' => [
            'store_id' => '0',
            'code' => 'admin',
            'website_id' => '0',
            'group_id' => '0',
            'name' => 'Admin',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'default' => [
            'store_id' => '1',
            'code' => 'default',
            'website_id' => '1',
            'group_id' => '1',
            'name' => 'Default Store View',
            'sort_order' => '0',
            'is_active' => '1',
        ],
        'site2sv' => [
            'store_id' => '2',
            'code' => 'site2sv',
            'website_id' => '2',
            'group_id' => '2',
            'name' => 'Second Website Store view',
            'sort_order' => '0',
            'is_active' => '1',
        ],
    ],
]
```

Ciò significa che in passato hai impostato [SCD sulla build](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/deploy/static-content#setting-the-scd-on-build) eseguendo il comando `config:dump` nel pacchetto `ece-tools`.

Se il nuovo archivio o sito Web creato non viene visualizzato nel file `app/etc/config.php`, eseguire nuovamente il comando per sincronizzare il file `config.php` con le modifiche apportate al database, quindi eseguire il commit del file `config.php` e ridistribuirlo. Questo consente di facilitare la distribuzione di contenuti statici per i nuovi store o siti Web nei percorsi di file appropriati.

## Lettura correlata

* [Configura più siti Web o store: Aggiungi nuovo [!DNL Domains]](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=it#add-new-domains) nella nostra guida utente.
* [Sito non accessibile a causa del cloaking dell&#39;origine](https://experienceleague.adobe.com/it/docs/experience-cloud-kcs/kbarticles/ka-26856)
