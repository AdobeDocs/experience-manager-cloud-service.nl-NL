---
title: AEM Forms as a Cloud Service - Communicatie
description: Automatisch gegevens samenvoegen met XDP- en PDF-sjablonen of uitvoer genereren in PCL-, ZPL- en PostScript-indelingen
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: 07b9118b8cfc27bc9e2bfa134fbb57c7ae2728ad
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---


# Synchrone verwerking gebruiken {#sync-processing-introduction}

Met behulp van communicatie kunt u merkgeoriënteerde en gepersonaliseerde communicatie maken, samenstellen en leveren, zoals zakelijke correspondentie, documenten, instructies, claimverwerkingsbrieven, aankondigingen van voordelen, claimverwerkingsbrieven, maandelijkse facturen en welkomstkits. U kunt Communicatie APIs gebruiken om een malplaatje (XFA of PDF) met klantengegevens te combineren om documenten in PDF, PS, PCL, DPL, IPL, en ZPL formaten te produceren.

Overweeg een scenario waar u één of meerdere malplaatjes en veelvoudige verslagen van de gegevens van XML voor elke malplaatje hebt. U kunt communicatie-API&#39;s gebruiken om een afdrukdocument te genereren voor elke record. <!-- You can also combine the records into a single document. --> Het resultaat is een niet-interactief PDF-document. In een niet-interactief PDF-document kunnen gebruikers geen gegevens invoeren in de desbetreffende velden.


De mededelingen verstrekken APIs voor het op bestelling en geplande documentgeneratie. U kunt synchrone API&#39;s voor asynchrone API&#39;s (Asynchrone API&#39;s) voor het genereren van geplande documenten gebruiken:

* Synchrone API&#39;s zijn geschikt voor gebruik op aanvraag, met lage latentie en het genereren van documenten met één record. Deze API&#39;s zijn geschikter voor gebruiksgevallen die zijn gebaseerd op gebruikersacties. Het genereren van een document bijvoorbeeld nadat een gebruiker een formulier heeft ingevuld.

* Batch-API&#39;s (Asynchrone API&#39;s) zijn geschikt voor geplande toepassingen waarbij meerdere documenten met hoge doorvoer worden gegenereerd. Deze API&#39;s genereren documenten batchgewijs. Zo worden telefoonrekeningen, creditcardafschriften en uitkeringsafschriften elke maand gegenereerd.

## Synchrone bewerkingen gebruiken {#batch-operations}

Een synchrone bewerking is een proces waarbij documenten lineair worden gegenereerd. Afzonderlijke API&#39;s zijn beschikbaar voor:

* Hiermee genereert u een PDF-document op basis van een sjabloon en voegt u er gegevens aan toe.
* Genereer een PostScript- (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL)-document op basis van een XDP-bestand of PDF-document.
* PDF-documenten samenstellen
* PDF-documenten demonteren
* Een document converteren naar een document dat voldoet aan de PDF/A-standaard
* Een document valideren dat voldoet aan de PDF/A-standaard


### Een API-aanroep verifiëren

De synchrone verrichtingen steunen twee type van authentificatie:

* **Basisverificatie**: De basisauthentificatie is een eenvoudige authentificatieregeling die in het protocol van HTTP wordt gebouwd. De client verzendt HTTP-aanvragen met de machtigingsheader die het woord Basic bevat, gevolgd door een spatie en een base64-coded tekenreeks username:password. Als u bijvoorbeeld autoriseert als beheerder/beheerder, verzendt de client Basic [base64-coded string username]: [base64-gecodeerd tekenreekswachtwoord].

* **Tokengebaseerde verificatie:** De op token-gebaseerde authentificatie gebruikt een toegangstoken (het teken van de authentificatie van de Drager) om verzoeken aan Experience Manager as a Cloud Service te maken. AEM Forms as a Cloud Service verstrekt APIs om het toegangstoken veilig terug te winnen. Om het teken terug te winnen en te gebruiken om een verzoek voor authentiek te verklaren:

   1. [as a Cloud Service referenties van Experience Manager ophalen uit de ontwikkelaarsconsole](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. [as a Cloud Service referenties van Experience Manager installeren op uw omgeving](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html). (De Server van de Toepassing, de Server van het Web, of andere niet-AEM servers) die worden gevormd om verzoeken naar (maken vraag) de wolkendienst te verzenden.
   1. [Een JWT-token genereren en deze uitgewisseld met Adobe IMS API&#39;s voor een toegangstoken](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. Voer de Experience Manager-API met het toegangstoken uit als een token voor Dragerverificatie.
   1. [Stel de juiste machtigingen in voor de gebruiker van de technische account in de Experience Manager-omgeving](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=en#configure-access-in-aem).

   >[!NOTE]
   >
   >Adobe raadt aan tokenverificatie op een productieomgeving te gebruiken.


### (Alleen voor API&#39;s voor documentgeneratie) Elementen en machtigingen configureren

Voor het gebruik van synchrone API&#39;s is het volgende vereist:

* PDF- of XDP-sjablonen
* [Gegevens die met sjablonen moeten worden samengevoegd](#form-data)
* Gebruikers met beheerdersrechten voor Experience Managers
* Sjablonen en andere elementen uploaden naar uw Experience Manager Forms Cloud Service-exemplaar

### (Alleen voor API&#39;s voor documentgeneratie) Sjablonen en andere elementen uploaden naar uw Experience Manager-instantie

Een organisatie heeft doorgaans meerdere sjablonen. Bijvoorbeeld, één malplaatje elk voor creditcardverklaringen, voordelenverklaringen, en claimtoepassingen. Upload al dergelijke XDP en PDF malplaatjes aan uw instantie van de Experience Manager. Een sjabloon uploaden:

1. Open een Experience Manager-instantie.
1. Ga naar Forms > Forms en Documenten
1. Klik op Maken > Map en maak een map. Open de map.
1. Klik op Maken > Bestand uploaden en upload de sjablonen.


### Een API aanroepen

De [API-naslagdocumentatie](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/) verstrekt gedetailleerde informatie over alle parameters, authentificatiemethodes, en diverse diensten die door APIs worden verleend. De API-naslagdocumentatie biedt ook een API-definitiebestand in de indeling .yaml. U kunt het .yaml dossier downloaden en het uploaden aan postman om functionaliteit van APIs te controleren.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>Alleen leden van een groep met formuliergebruikers hebben toegang tot communicatie-API&#39;s.
