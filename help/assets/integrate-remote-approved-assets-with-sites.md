---
title: AEM Assets op afstand integreren met AEM Sites
description: Leer hoe u AEM sites kunt configureren en verbinden met Approved AEM Assets in Creative Cloud.
source-git-commit: f6c0e8e5c1d7391011ccad5aa2bad4a6ab7d10c3
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---


# AEM Assets op afstand integreren met AEM Sites  {#integrate-approved-assets}

Het effectief beheren van digitale middelen is van cruciaal belang voor het aanbieden van aantrekkelijke en consistente merkervaringen op verschillende online platforms. Dynamic Media met OpenAPI-mogelijkheden verbetert het beheer van digitale middelen door naadloze integratie tussen AEM Sites en AEM Assets as a Cloud Service mogelijk te maken. Met deze vernieuwende functie kunt u eenvoudig verschillende typen goedgekeurde digitale elementen delen en beheren in meerdere AEM omgevingen, waardoor workflows voor siteauteurs en inhoudseditors worden gestroomlijnd.

Met Dynamic Media met OpenAPI-mogelijkheden kunnen siteauteurs middelen van externe DAM direct gebruiken in de AEM Page Editor en [Inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments.html), het vereenvoudigen van processen voor het maken en beheren van inhoud.

Gebruikers kunnen meerdere AEM Sites-instanties, zonder beperkingen op het maximumaantal, verbinden met een externe DAM-implementatie, wat een opmerkelijk voordeel is ten opzichte van de [Verbonden Assets](use-assets-across-connected-assets-instances.md) gebruiken.

![afbeelding](/help/assets/assets/connected-assets-rdam.png)

Na de eerste installatie kunnen gebruikers pagina&#39;s op het AEM Sites-exemplaar maken en zo nodig elementen toevoegen. Bij het toevoegen van elementen kunnen ze elementen selecteren die zijn opgeslagen in hun lokale DAM of door de middelen bladeren en gebruiken die beschikbaar zijn in de externe DAM.

Dynamic Media met OpenAPI-mogelijkheden biedt verschillende andere voordelen, zoals toegang tot en gebruik van externe middelen in Content Fragment, het ophalen van metagegevens van de externe middelen en nog veel meer. Meer weten over de andere [voordelen van Dynamic Media met OpenAPI-mogelijkheden via Connected Assets](/help/assets/dynamic-media-open-apis-faqs.md).

## Voordat u begint {#pre-requisits-sites-integration}

* Het volgende instellen [omgevingsvariabelen](/help/implementing/cloud-manager/environment-variables.md#add-variables) voor AEM as a Cloud Service:

   * ASSET_DELIVERY_REPOSITORY_ID= &quot;delivery-pxxxxx-eyyyyy.adobeaemcloud.com&quot; <br>
     `pXXXX` verwijst naar de programma-id <br>
     `eYYYY` verwijst naar de milieu-id

   * ASSET_DELIVERY_IMS_CLIENT= [IMSClientId]

  of configureer de [OSGi-instellingen](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi.html) voor AEM 6.5 in de AEM Sites-instantie door de volgende stappen te volgen:

   1. Aanmelden bij de console en klikken op **[!UICONTROL OSGi]>** of gebruik de directe URL, bijvoorbeeld: `http://localhost:4502/system/console/configMgr`

   1. Voeg de **[!UICONTROL repositoryID]**= &quot;delivery-pxxxxx-eyyyyy.adobeaemcloud.com&quot; en **[!UICONTROL imsClient]**= [IMSClientId]
Meer informatie over [IMS-verificatie](https://experienceleague.adobe.com/docs/experience-manager-65/content/security/ims-config-and-admin-console.html).

* IMS-toegang om u aan te melden bij een externe DAM AEM as a Cloud Service-instantie.

* Schakel de schakeloptie Dynamic Media met OpenAPI-mogelijkheden in op de externe DAM.

* Configureer de component Image v3 in de AEM Sites-instantie. Als de component niet aanwezig is, download en installeer het [inhoudspakket](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.23.0).

## Elementen benaderen vanaf externe DAM {#fetch-assets}

Met Dynamic Media met OpenAPI-mogelijkheden hebt u toegang tot middelen die beschikbaar zijn in uw externe DAM-instantie in uw lokale AEM Sites Page Editor en AEM Content Fragment.

![afbeelding](/help/assets/assets/open-APIs.png)

### Externe elementen openen in AEM paginaeditor {#access-assets-page-editor}

Voer de onderstaande stappen uit om externe middelen te gebruiken in AEM Pagina-editor voor uw AEM Sites-exemplaar. U kunt deze integratie doen in AEM as a Cloud Service en AEM 6.5.

1. Ga naar **[!UICONTROL Sites]** > _uw website_ waar de AEM **[!UICONTROL Page]** is aanwezig waarbinnen u het externe element moet toevoegen.
1. Naar de specifieke AEM navigeren **[!UICONTROL Page]** binnen uw website onder **[!UICONTROL Sites]** -sectie waar u het externe element wilt toevoegen.
1. Selecteer de pagina en klik op **[!UICONTROL Edit (_e _)]**. De AEM **[!UICONTROL Page Editor]**wordt geopend.
1. Klik op de container voor lay-out en voeg een **[!UICONTROL Image]** component.
1. Klik op de knop **[!UICONTROL Image]** component en klik op ![instellingenpictogram](/help/assets/assets/do-not-localize/settings-icon.svg) pictogram.
1. Schakel het selectievakje **[!UICONTROL Inherit featured image from page]** -optie.
1. Klikken **[!UICONTROL Pick]** en selecteert u **[!UICONTROL Remote]**.
   ![afbeelding](/help/assets/assets/uncheck-inherit-option.jpg)

   U wordt gevraagd u aan te melden.
1. Selecteer het element en klik op **[!UICONTROL Select]**.
1. Een alternatieve tekst toevoegen en klikken **[!UICONTROL Done]**.
   <br> Het externe element wordt weergegeven in de afbeeldingscomponent. U kunt ook de URL van levering van het element controleren wanneer het op de pagina wordt geladen of via het tabblad Voorbeeld. De leverings-URL geeft aan dat het element op afstand wordt benaderd.

U hebt alleen toegang tot externe middelen in AEM pagina-editor voor Image Core Component v3 en Teaser Core Component v2. Voor andere componenten, waaronder aangepaste componenten, zijn aanpassingen vereist om Asset Selector met deze componenten te integreren.

#### Video: Externe elementen openen in AEM Pagina-editor

>[!VIDEO](https://video.tv.adobe.com/v/3427666)

### Externe elementen openen in AEM inhoudsfragment {#access-assets-content-fragment}

Voer de onderstaande stappen uit om Externe elementen te gebruiken in AEM inhoudsfragment op uw AEM Sites-exemplaar. U kunt deze integratie uitvoeren in AEM 6.5 en niet in AEM as a Cloud Service.

1. Ga naar **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Selecteer een elementmap waarin het inhoudsfragment zich bevindt.
1. Selecteer het inhoudsfragment en klik op **[!UICONTROL Edit (_e _)]**.

   >[!NOTE]
   >
   >Als u geen AEM model van het Fragment van de Inhoud hebt, kunt u moeten [één maken](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments-models.html?lang=en).

1. Klik op de knop ![pictogram vinkje](/help/assets/assets/do-not-localize/checkmark-icon.svg) naast de tekstcomponent.
1. Selecteren **[!UICONTROL Remote]** om de middelen van verre DAM te halen. <br>
U kunt kiezen **[!UICONTROL Local]** of **[!UICONTROL Remote]** DAM-opslagplaats op basis van uw behoeften.

   ![image](/help/assets/assets/cf-pick.jpg)
U wordt gevraagd u aan te melden.
1. Kies het element en klik op **[!UICONTROL Select]**.
   <br> De URL van het externe element wordt weergegeven in de tekstcomponent.

#### Video: Externe elementen benaderen in AEM inhoudsfragment

>[!VIDEO](https://video.tv.adobe.com/v/3427667)

### Externe middelen openen in Edge Delivery Services {#access-assets-eds}

U kunt externe elementen ook benaderen in Edge Delivery Services. Zie voor meer informatie [Elementen van Assets as a Cloud Service gebruiken die met Dynamic Media zijn geleverd met OpenAPI-mogelijkheden](https://www.aem.live/docs/aem-assets-sidekick-plugin#utilizing-assets-from-assets-cloud-services-delivered-via-dynamic-media-with-openapi).
