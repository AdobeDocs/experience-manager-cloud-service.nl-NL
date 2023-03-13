---
title: Verbinding maken met Microsoft Translator
description: Leer hoe u AEM kunt verbinden met Microsoft Translator vanuit de verpakking om uw vertaalworkflow te automatiseren.
feature: Language Copy
role: Admin
exl-id: ca3c50f9-005e-4871-8606-0cfd3ed21936
source-git-commit: d925310603961f1f3721c283fc247105459e9c0f
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# Verbinding maken met Microsoft Translator {#connecting-to-microsoft-translator}

Een configuratie maken voor de [Microsoft Vertaler](https://www.microsoft.com/en-us/translator/business/) cloudservice waarmee u uw Microsoft-vertaalaccount kunt gebruiken voor het vertalen van AEM pagina-inhoud of -elementen.

>[!TIP]
>
>Als u nog geen ervaring hebt met het vertalen van inhoud, raadpleegt u onze [Sites Translation Journey,](/help/journey-sites/translation/overview.md) Dit is een geleid pad door uw AEM Sites-inhoud te vertalen met de krachtige vertaalgereedschappen van AEM, ideaal voor mensen zonder AEM of vertaalervaring.

>[!NOTE]
>
>AEM levert een proefaccount voor Microsoft-vertaling, waarbij maximaal 2 000 000 gratis vertaalde tekens per maand zijn toegestaan. Als u een accountabonnement wilt verkrijgen dat geschikt is voor productiesystemen, raadpleegt u [De Microsoft Translator-licentieconfiguratie voor proefversies bijwerken](#upgrading-the-microsoft-translator-trial-license-configuration).

| Eigenschap | Beschrijving |
|---|---|
| Vertaallabel | De weergavenaam voor de vertaalservice |
| Vertaalkenmerk | (Optioneel) Voor door de gebruiker gegenereerde inhoud wordt bijvoorbeeld de toewijzing naast vertaalde tekst weergegeven `Translations by Microsoft` |
| Werkruimte-id | (Optioneel) De id van de aangepaste Microsoft Translator-engine die u wilt gebruiken |
| Subscription Key | Je Microsoft Subscription Key voor Microsoft Translator |

Nadat u de configuratie creeert, moet u [activeren](#activating-the-translator-service-configurations).

De volgende procedure leidt tot een configuratie van de Vertaler van Microsoft.

1. In de [navigatievenster,](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps) klikken of tikken **Gereedschappen** -> **Cloud Services** -> **Cloud Services voor vertaling**.
1. Navigeer naar de locatie waar u de configuratie wilt maken. Normaal gesproken bevindt dit zich in de hoofdmap van de site of kan het een algemene standaardconfiguratie zijn.
1. Tik of klik op de knop **Maken** knop.
1. Definieer uw configuratie.
   1. Selecteren **Microsoft Vertaler** in de vervolgkeuzelijst.
   1. Typ een titel voor de configuratie. De titel identificeert de configuratie in de console van Cloud Services evenals in de drop-down lijsten van het paginabezit.
   1. Typ desgewenst een naam die u wilt gebruiken voor het knooppunt in de opslagplaats dat de configuratie opslaat.

   ![Vertaalconfiguratie maken](../assets/create-translation-config.png)

1. Klikken **Maken**.
1. In de **Configuratie bewerken** Geef de waarden voor de vertaalservice op die in de vorige tabel zijn beschreven.

   ![Vertaalconfiguratie bewerken](../assets/edit-translation-config.png)

1. Tik of klik op **Verbinden** om de verbinding te verifiëren.
1. Tik of klik op **Opslaan en sluiten**.

## De Microsoft Translator-licentieconfiguratie voor proefversies bijwerken {#upgrading-the-microsoft-translator-trial-license-configuration}

Microsoft-vertaalconfiguratiepagina&#39;s bieden een handige koppeling naar de Microsoft-website voor het verkrijgen van een accountabonnement dat geschikt is voor productiesystemen.

1. In de [navigatievenster,](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps) tikken of klikken **Gereedschappen** -> **Cloud Services** -> **Cloud Services voor vertaling**.
1. Tik of klik op de bestaande Microsoft Translator-configuratie.
1. Tik of klik op **Bewerken**.
1. In de **Configuratie bewerken** venster, tikken of klikken **Abonnement voor upgrades**. Er wordt een Microsoft-webpagina met meer informatie over de service geopend.

## De Microsoft Translator Engine aanpassen {#customizing-your-microsoft-translator-engine}

Microsoft Translation Configuration-pagina&#39;s bieden een handige koppeling naar de Microsoft-website om uw Microsoft Translator-engine aan te passen.

1. In de [navigatievenster,](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps) tikken of klikken **Gereedschappen** -> **Cloud Services** -> **Cloud Services voor vertaling**.
1. Tik of klik op de bestaande Microsoft Translator-configuratie.
1. Tik of klik op **Bewerken**.
1. In de **Configuratie bewerken** venster, tikken of klikken **Vertaler aanpassen**. Gebruik de Microsoft-webpagina die wordt geopend om uw service aan te passen.

## De configuraties van de vertaalservice activeren {#activating-the-translator-service-configurations}

U moet uw configuraties van de wolkendienst activeren om vertaalde inhoud te steunen die aan de publicatie instantie wordt herhaald. Gebruik de methode [publiceren, boomstructuur](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#publishing-and-unpublishing-a-tree) om de opslagknooppunten te activeren die de Microsoft Translator-configuraties opslaan. De knooppunten bevinden zich onder de volgende bovenliggende knooppunten:

* `/libs/settings/cloudconfigs/translation/msft-translation`
