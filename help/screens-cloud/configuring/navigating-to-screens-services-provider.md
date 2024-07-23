---
title: Navigeren naar Screens Services Provider
description: In deze pagina wordt beschreven hoe u naar Screens Services Provider kunt navigeren.
exl-id: 9eff6fe8-41d4-4cf3-b412-847850c4e09c
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: 093cd62f282bd9842ad74124bb9bd4d5a33ef1c5
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 1%

---

# Navigeren naar Screens Services Provider {#setup-screens-services-provider}

## Inleiding {#introduction}

**Screens Services Provider**, staat de inhoudauteur, de ontwikkelaars, en de beheerders toe om vertoningen en spelers voor inhoudsplayback te beheren zodra de inhoud aan de kanalen wordt toegevoegd. Zodra de gebruikers toegang tot AEM Cloud Service krijgen, moeten zij zich kunnen aanmelden bij de Screens Services Provider.

In deze sectie wordt beschreven hoe u Screens Services Provider kunt instellen.


## Doelstelling {#objective}

De volgende sectie om de Leverancier van de Diensten van Screens te vormen en te vestigen.

## Stappen om Screens Services Provider in te stellen {#screens-services-provider}

Voer de onderstaande stappen uit om Screens Services Provider in te stellen:

1. Navigeer aan de Leverancier van de Diensten van Screens van [ hier ](https://experience.adobe.com/screens).

   >[!CAUTION]
   >Als u toegang tot veelvoudige organisaties hebt, zorg ervoor dat u in correcte Organisatie hebt geregistreerd. Als u uw organisatie wilt wijzigen, klikt u op de naam van de organisatie in de rechterbovenhoek van het scherm en kiest u de gewenste organisatie waartoe u toegang nodig hebt.

1. Klik op het tandwielpictogram naast Project (linkerbovenhoek)

   ![afbeelding](/help/screens-cloud/assets/configure/configure-screens0.png)

1. Voer in het dialoogvenster Instellingen bewerken de volgende gegevens in.
   * **URL van Publish** - AEM publiceert URL (bijvoorbeeld, `https://publish-p12345-e12345.adobeaemcloud.com`)
   * **Auteur URL** - AEM auteur URL (bijvoorbeeld, `https://author-p12345-e12345.adobeaemcloud.com`)

   >[!NOTE]
   >Zorg ervoor dat u ten minste één AEM-schermkanaal maakt en publiceert voordat u de AEM onder Screens Service Provider configureert. Als u een kanaal wilt maken, navigeert u naar /screens.html op uw inhoudsprovider.

   ![afbeelding](/help/screens-cloud/assets/configure/configure-screens4.png)

1. Klik **sparen** om met de inhoudsleverancier van Screens te verbinden.

1. In u hebt AEM gevormd publiceer instantie om toegang slechts tot vertrouwde op IP adressen door de eigenschap van de Lijst van gewenste personen van de Cloud Manager IP toe te staan, moet u een kopbal met een zeer belangrijke waarde in de instellingendialoog zoals hieronder getoond vormen.
IPs die aan whitelisted ook moet worden bewogen aan het configuratiedossier en moet [ niet worden toegepast ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/apply-allow-list) van de montages van Cloud Manager zijn.

   ![ beeld ](/help/screens-cloud/assets/configure/configure-screens20.png)
De zelfde sleutel moet bij AEM configuratie worden gevormd CDN.  Het wordt geadviseerd om de kopbalwaarde niet direct in GITHub te zetten en a [ geheime verwijzing ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-credentials-authentication#rotating-secrets) te gebruiken.
Een steekproef [ CDN config ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/traffic-filter-rules-including-waf) wordt hieronder gegeven:
kind: &quot;CDN&quot;
version: &quot;1&quot;
metagegevens:
envTypes: [ &quot;dev&quot;, &quot;stage&quot;, &quot;prod&quot;]
gegevens:
trafficFilters:
regels:
- naam: &quot;block-request-from-not-allowed-ips&quot;
wanneer:
allOf:
- reqProperty: clientIp
notIn: [ &quot;101.41.112.0/24&quot;]
reqProperty: tier
is gelijk aan: publiceren
handeling: blok
- naam: &quot;allow-request-with-header&quot;
wanneer:
allOf:
- reqProperty: tier
is gelijk aan: publiceren
- reqProperty: path
equals: /screens/channels.json
- reqHeader: x-screens-lijst van gewenste personen-key
equals: $\
   {CDN_HEADER_KEY}
handeling:
type: toestaan

1. Selecteer **Kanalen** van de linkernavigatiebar en klik **open in inhoudsleverancier**.

   ![afbeelding](/help/screens-cloud/assets/configure/configure-screens1.png)

1. De Screens Content Provider wordt geopend op een ander tabblad waarop u uw inhoud kunt maken.

   ![afbeelding](/help/screens-cloud/assets/configure/configure-screens2.png)





## Volgende functies {#whats-next}

Nadat u hebt geleerd hoe te opstelling de Leverancier van de Diensten van Screens, navigeer aan [ Gebruikend de Leverancier van de Inhoud van Screens ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html#screens-content-provider) voor meer details.
