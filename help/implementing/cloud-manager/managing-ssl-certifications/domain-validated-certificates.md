---
title: DV-certificaten (Domain Validated)
description: Leer hoe u DV-certificaten (Domain Validated) in Cloud Manager beheert.
exl-id: 7f2c71b6-15c3-4919-9f51-a3e26d0d48d4
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# DV-certificaten (Domain Validated) {#domain-validated-certificates}

Leer hoe u DV-certificaten (Domain Validated) in Cloud Manager beheert.

>[!NOTE]
>
>Deze eigenschap is slechts beschikbaar aan [ het vroege adopterprogramma.](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)

## Inleiding {#introduction}

Met Cloud Manager kunt u op zelfbediening een DV (Domain Validated SSL Certificate) genereren en beheren. Dit biedt u de snelste, eenvoudigste en voordeligste oplossing om een veilige website voor uw online bedrijf te maken.

De domein bevestigde certificaten zijn beschikbaar aan zowel [ productie als zandbakprogramma&#39;s.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

## Een aangepast domein toevoegen {#adding-domain}

Als u een DV-certificaat (Domain Validated) wilt toevoegen, moet u eerst het aangepaste domein configureren. Het proces is grotendeels het zelfde als gedetailleerd in het document [ Inleiding aan de Namen van het Domein van de Douane.](/help/implementing/cloud-manager/custom-domain-names/introduction.md) Deze functionaliteit is echter enigszins uitgebreid.

1. Wanneer het verifiëren van het domein, kunt u verkiezen om Adobe-geleide of zelf-beheerde certificaten met het domein te gebruiken. Kies **Adobe beheerde certificaat** om een DV- certificaat later toe te voegen.

   ![ kies Adobe-geleid ](assets/verify-domain-dialog.png)

1. Om een Adobe te gebruiken beheerde certificaat, moet u een verslag CNAME aan uw DNS toevoegen zoals die in **wordt beschreven verifieer domein** dialoog.

   ![ voeg de ingang van CNAME ](assets/verify-domain-dialog-adobe-managed.png) toe

1. Zodra het domein wordt gecreeerd, tik of klik de ellipsknoop in de lijst van domeinen en selecteer **verifieer** om het domein te verifiëren.

   ![ verifieer domein ](assets/verify-domain.png)

## Een DV-certificaat toevoegen {#adding}

Zodra u uw domein correct hebt gevormd, om een DV- certificaat toe te voegen, onttikt of klikt **SSL certificaat** knoop in het SSL venster van Certificaten toevoegen.

![ Toevoegend een certificaat van gelijkstroom ](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

1. Selecteer de optie **beheerde Adobe (DV)**.
1. Specificeer de domeinnaam in **Uitgezochte domeinen** drop down.
1. Tik of klik **sparen**.

Zodra met succes toegevoegd zal het certificaat een hangende status met een geel waarschuwingsbord aan zijn naam in het **SSL venster van Certificaten** hebben.

![ Hangende DV cert ](assets/pending-dv-certificate.png)

Zodra met succes uitgegeven zal het certificaat een groen vinkje aan zijn naam in het **SSL venster van Certificaten** hebben.

![ Uitgegeven DV cert ](assets/issued-dv-certificate.png)

Voor meer informatie over het toevoegen van SSL certificaten en het SSL venster van Certificaten, te zien gelieve het document [ Toevoegend een SSL Certificaat.](add-ssl-certificate.md)

## CDN-configuratie toevoegen {#add-cdn}

Deze stap moet worden voltooid om een domein met SSL te vormen gebruikend Fastly CDN.

Ga als volgt te werk om een CDN-configuratie toe te voegen met Cloud Manager.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Selecteer het **lusje van de Configuraties 0} CDN en klik of tik** **in de hulpmiddelbar toevoegen.**

1. In **vorm CDN** dialoog, verstrek de noodzakelijke informatie.

   * Selecteer de **Oorsprong**. Dit kan zijn:
      * Een omgeving met Cloud Servicen
      * Een site voor Edge Delivery Services
   * Selecteer het CDN-type.
   * Selecteer het domein.
   * Selecteer het SSL-certificaat.
      * Slechts vereist voor Adobe-geleide CDNs.

   ![ vorm CDN dialoog ](assets/configure-cdn-dialog.png)

>
>
>Voor Adobe-geleide CDNs, wanneer het gebruiken van DV certificaten, slechts worden de plaatsen met de bevestiging van ACME toegelaten.
