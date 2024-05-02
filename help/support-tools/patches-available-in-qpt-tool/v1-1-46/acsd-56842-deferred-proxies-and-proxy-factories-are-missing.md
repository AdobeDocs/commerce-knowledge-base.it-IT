---
title: '"ACSD-56842: i proxy differiti e le factory proxy non sono presenti dopo l’esecuzione di "setup":di:compila`'''
description: Applica la patch ACSD-56842 per risolvere il problema Adobe Commerce, in cui i proxy e le factory proxy differiti risultano mancanti dopo l’esecuzione di `setup:di:compila".
feature: Deploy, Catalog Management
role: Admin, Developer
exl-id: 2d12e36c-d8b7-4253-91d8-28b50477ccd9
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-56842: proxy differiti e factory proxy mancanti dopo l&#39;esecuzione `setup:di:compile`

La patch ACSD-56842 risolve il problema relativo alla mancanza di proxy e factory proxy dopo l&#39;esecuzione `setup:di:compile`. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46. L’ID della patch è ACSD-56842. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I proxy e le factory proxy differiti sono mancanti dopo l&#39;esecuzione `setup:di:compile`.

<u>Passaggi da riprodurre</u>:

1. Creare un modulo personalizzato denominato *Magento_CustomModule*.
1. In *[!UICONTROL etc]* del modulo, crea un `di.xml` con questo contenuto:

   ```xml
    <?xml version="1.0"?>
     <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
        <type name="Magento\Catalog\Model\ProductLink\CollectionProvider">
           <arguments>
              <argument name="providers" xsi:type="array">
                 <item name="crosssell" xsi:type="object">
                      Magento\Catalog\Model\ProductLink\CollectionProvider\Crosssell\Proxy
                 </item>
                   <item name="upsell" xsi:type="object">Magento\Catalog\Model\ProductLink\CollectionProvider\Upsell\Proxy</item>
                     <item name="related" xsi:type="object">Magento\Catalog\Model\ProductLink\CollectionProvider\Related\Proxy</item>
              </argument>
           </arguments>
         </type>
            <type name="Magento\Catalog\Model\Product">
               <arguments>
                  <argument name="catalogProductStatus" xsi:type="object">
                   Magento\Catalog\Model\Product\Attribute\Source\Status\Proxy
                  </argument>
                   <argument name="productLink" xsi:type="object">
                     Magento\Catalog\Model\Product\Link\Proxy
                   </argument>
               </arguments>
             </type>
     </config>
   ```

1. Imposta il [!UICONTROL Production] modalità: `bin/magento deploy:mode:set production`.
1. Elimina la cartella generata dalla directory principale di Magento.
1. Esegui il comando `bin/magento setup:di:compile`.
1. Controlla la cartella generata.

<u>Risultati previsti</u>:

* I file proxy vengono creati correttamente dopo la compilazione.
* I file di factory vengono creati correttamente dopo la compilazione.

<u>Risultati effettivi</u>:

Nella cartella generata, il file proxy viene generato per gli argomenti proxy forniti senza interruzioni di riga e non per gli argomenti forniti con interruzioni di riga.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
