---
title: Veelgestelde vragen over HTTP2-levering van content
description: Meer informatie over de levering van HTTP2-inhoud.
contentOwner: Rick Brough
role: Admin,User
exl-id: 0a8a5fd8-a341-4e7f-84a5-409e2de97efe
source-git-commit: b37ff72dbcf85e5558eb3421b5168dc48e063b47
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 1%

---

# Veelgestelde vragen over HTTP2-levering van content{#http-delivery-of-content-faq}

Adobe is opgetogen om de beschikbaarheid van HTTP/2 levering van inhoud aan te kondigen. Bij gebruik van HTTP/2 wordt een algehele prestatieverhoging ervaren.

>[!NOTE]
>
>Deze functie vereist dat u het out-of-the-box Content Delivery Network gebruikt dat is gebundeld met Adobe Experience Manager - Dynamic Media. Een ander netwerk voor de levering van aangepaste inhoud wordt niet ondersteund met deze functie.

## Wat is HTTP/2? {#what-is-http}

HTTP/2 verbetert de manier waarop browsers en servers communiceren, waardoor informatie sneller kan worden overgedragen en de benodigde hoeveelheid verwerkingskracht wordt verminderd.

Het websiteartikel [Wat u moet weten over HTTP/2](https://www.engadget.com/2015-02-24-what-you-need-to-know-about-http-2.html) beschrijft HTTP/2 en zijn voordelen op een korte en eenvoudige manier.

## Wat zijn de belangrijkste voordelen van de overgang naar HTTP/2 voor de levering van inhoud? {#what-are-the-key-benefits-of-moving-to-http-for-content-delivery}

Prestatieverbetering varieert sterk, omdat deze op verschillende factoren is gebaseerd. Bijvoorbeeld de code van uw website, hoe u Dynamic Media gebruikt, het apparaat van de consument, het scherm, en de plaats.

Resultaten:

* Voor afbeeldingen verbeterde de responstijd 7%-28%, afhankelijk van het apparaat en de browser. De meest opmerkelijke prestatiewinst was op iOS-apparaten.
* Voor viewers verbeterde de laadtijd tot 15%.

De volgende demonstratie illustreert het verschil tussen het laden van HTTP/1 en HTTP/2:

[https://http2.akamai.com/demo](https://http2.akamai.com/demo)

## Mag ik overschakelen op HTTP/2? {#am-i-eligible-to-switch-over-to-http}

Als u HTTP/2 wilt gebruiken, moet u aan de volgende vereisten voldoen:

* Gebruik beveiligde HTTPS voor uw rich media-aanvragen.
* Gebruik de Adobe-gebundelde CDN (Content Delivery Network) als onderdeel van uw Dynamic Media Classic-licentie.
* Gebruik een speciaal domein (dat wil zeggen `images.company.com` of `mycompany.scene7.com`), niet een algemeen Dynamic Media-domein (dat wil zeggen: `s7d1.scene7.com`, `s7d2.scene7.com`, of `s7d13.scene7.com`).

   Om uw domeinen te vinden, open [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)en meld u vervolgens aan bij uw account.

   Ga naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]**. Zoeken naar het veld met het label **Gepubliceerde servernaam**. Als u momenteel een algemeen Dynamic Media-domein gebruikt, kunt u vragen dat u in het kader van deze overgang overschakelt naar uw eigen aangepaste domein.

## Wat is het proces voor het inschakelen van HTTP/2 voor mijn Dynamic Media-account? {#what-is-the-process-for-enabling-http-for-my-dm-account}

[Gebruik de Admin Console om een steungeval tot stand te brengen](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) en verzoek om over te schakelen op HTTP/2; het wordt niet automatisch voor u gedaan.

1. Geef de volgende informatie op in uw ondersteuningsgeval:

   * Primaire contactpersoon, e-mail en telefoonnummer.
   * Alle domeinen die naar HTTP2 moeten worden overgebracht. Dat wil zeggen: `images.company.com` of `mycompany.scene7.com`.

   Om uw domeinen te vinden, open [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)en meld u vervolgens aan bij uw account.

   Ga naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]**. Zoeken naar het veld met het label **[!UICONTROL Published Server Name]**.

   * Controleer of u beveiligde HTTPS gebruikt voor aanvragen voor rich media.
   * Verifieer u CDN door Adobe gebruikt en niet beheerd met een directe verhouding.
   * Controleer of u een specifiek domein gebruikt. Dat wil zeggen: `images.company.com` of `mycompany.scene7.com`, geen algemeen Dynamic Media-domein zoals `s7d1.scene7.com`, `s7d2.scene7.com`, `s7d13.scene7.com`.

   Als u uw domeinen wilt zoeken, opent u het dialoogvenster [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)en meld u vervolgens aan bij uw account.

   Ga naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]**. Zoeken naar het veld met het label **[!UICONTROL Published Server Name]**. Als u momenteel een algemeen Dynamic Media-domein gebruikt, kunt u vragen dat u in het kader van deze overgang overschakelt naar uw eigen aangepaste domein.

   1. De Steun van de klant voegt u aan de HTTP/2 klantenwachtlijst toe die op de orde wordt gebaseerd waarin de verzoeken werden voorgelegd.
   1. Wanneer Adobe bereid is om uw verzoek te behandelen, contacteert de Steun van de Klant u om de overgang te coördineren en een doeldatum te plaatsen.
   1. U wordt op de hoogte gesteld nadat de bewerking is voltooid en u kunt controleren of de overgang naar HTTP2 is gelukt.



## Wanneer kan ik verwachten over te gaan naar HTTP/2? {#when-can-i-expect-to-be-transitioned-over-to-http}

Verzoeken worden verwerkt in de volgorde waarin ze door Customer Support worden ontvangen.

>[!NOTE]
>
>Er is een lange aanlooptijd omdat de overgang naar HTTP/2 het wissen van de cache omvat. Daarom kunnen slechts een paar klantenovergangen tegelijkertijd worden behandeld.

## Wat zijn de risico&#39;s bij de overgang naar HTTP/2? {#what-are-the-risks-with-moving-to-http}

De overgang aan HTTP/2 ontruimt uit uw geheime voorgeheugen bij CDN omdat het het bewegen aan een nieuwe configuratie CDN impliceert.

De inhoud in de cache raakt de servers van Adobe die niet in de cache zijn opgeslagen, rechtstreeks aan. Wegens deze actie, is Adobe van plan om een paar klantenovergangen in een tijd te behandelen. Deze methode zorgt ervoor dat aanvaardbare prestaties worden gehandhaafd wanneer het trekken van verzoeken van de oorsprong.

## Hoe kunt u controleren of een URL of website met HTTP/2 wordt geactiveerd? {#how-can-you-verify-whether-a-url-or-website-is-activated-with-http}

Download een extensie die u met uw webbrowser kunt gebruiken. Voor Firefox en Chrome is er een extensie genaamd **[!UICONTROL HTTP/2 and SPDY Indicator]**. Browsers ondersteunen alleen veilig HTTP/2, dus het is nodig een URL met HTTPS aan te roepen om te verifiëren. Als HTTP/2 wordt ondersteund, wordt dit aangegeven door de extensie in de vorm van een blauw Flash-symbool en een header &quot;X-Firefox-Spdy&quot;: &quot;h2&quot;.
