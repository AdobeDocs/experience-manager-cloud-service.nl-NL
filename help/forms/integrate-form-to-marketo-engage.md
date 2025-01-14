---
Title: How to Integrate Marketo Engage with AEM Forms?
Description: Learn how to integrate your Marketo Engage instance with AEM Forms.
Keywords: How to connect a Marketo instance with form? , Connect a form to Marketo, Integrate a form with Marketo Engage, Integrate an Adaptive Form with a Marketo instance.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 74cd25f9-1ee1-4f3f-8e02-8714071e7c86
source-git-commit: e46c5afac945620cc44e9064956848acecc786bf
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---

# Marketo Engage integreren met AEM Forms

<span class="preview"> De functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

Het integreren AEM Forms met [ Adobe Marketo Engage ](https://experienceleague.adobe.com/en/docs/marketo/using/home) laat gebruikers toe om de mogelijkheden van Marketo Engage te gebruiken om bedrijfslogica van gevangen gegevens tot stand te brengen en werkschema&#39;s, met inbegrip van slimme campagnes en e-mailautomatisering te automatiseren. Het geconfigureerde formulier kan vastgelegde gegevens naar het Marketo Engage verzenden voor verwerking.

## Voordelen van de integratie van Marketo Engage met formulieren

Hieronder ziet u enkele voordelen van het verbinden van een AEM met Adobe Marketo Engage:

* **Vereenvoudigde integratie**: Het verbinden van vormen met Marketo Engage elimineert de behoefte om een afzonderlijk model van vormgegevens tot stand te brengen. Het integratieproces is eenvoudig en gebruiksvriendelijk.
* **Geautomatiseerde gegevens vangen**: Het helpt in automatisch vormvoorlegging vangen en hen opslaan in Marketo, die handgegevensingang elimineren en fouten verminderen.

* **Lood beheer**: Het stroomlijnt lood beheersprocessen door vormvoorlegging direct in uw marketing gegevensbestand te integreren, toelatend beter het volgen en het koesteren van lood.

* **Verbeterde campagneprestaties**: Het gebruikt vormgegevens om marketing campagnes te analyseren en te optimaliseren, die algemene prestaties en rendement op investering (ROI) verbeteren.

* **Analytics en het melden**: Het helpt in het verkrijgen van toegang tot robuuste analytische en rapporteringshulpmiddelen, zoals Munchkin, binnen Marketo om de doeltreffendheid van vormen en campagnes te meten.

* **de automatisering van de follow-up**: Het helpt in het automatiseren van follow-up e-mail en werkschema&#39;s die door vormvoorlegging worden teweeggebracht, die geschikte mededeling met lood verzekeren.

## Belangrijkste voordelen van het gebruik van AEM Forms in plaats van alternatieve formulieroplossingen

In de onderstaande tabel worden de weinige redenen beschreven waarom u AEM Forms wilt kiezen in plaats van andere alternatieve formulieroplossingen:

| **Eigenschap** | **AEM Forms** | **Andere Oplossingen van de Vorm** |
|-------------------------------------|----------------------------------------------------------------------|-----------------------------------------------------------|
| **Aanpassingen** | Hiermee kunt u specifieke aangepaste functies toevoegen, formulierhandelingen aanpassen en veldgedrag wijzigen om de interactie van formulieren en complexe workflows te verbeteren | Geen aanpassingsondersteuning |
| **Redacteur van de Regel** | Steunt een ingebouwde Redacteur van de Regel voor het toevoegen van logica en voorwaarden. | Geen ondersteuning voor de regeleditor |
| **Opties van de Lay-out** | Ondersteunt meerdere lay-outopties | Beperkte layoutopties |
| **vooraf ingevulde Dienst** | Biedt een voorkeursservice voor het automatisch invullen van formuliergegevens. | Geen voorkeursservice beschikbaar |
| **Inbeddend in Plaatsen** | Kan in sites worden ingesloten met iFrame | Kan niet insluiten in sites met iFrame |
| **Versnelling van Integratie met Plaatsen** | Geen aanvullende training vereist; AEM Forms gebruikt dezelfde vaardigheden als Sites | Mogelijk is aanvullende training vereist |
| **Verzending van Gegevens** | Gegevens kunnen naar verschillende platforms worden verzonden en er zijn meerdere connectors beschikbaar, zoals Connect to SharePoint, Connect to OneDrive, Connect to Salesforce en meer. | Gegevens kunnen naar beperkte connectors worden verzonden, bijvoorbeeld naar Salesforce |

## Overwegingen bij de integratie van Marketo Engage met formulieren

Enkele overwegingen bij de integratie van Marketo Engage met AEM Forms:

* AEM ondersteunt alleen de People(Leads)-database tussen de verschillende Marketo-databases.
* Marketo staat de [ verwezenlijking van 10 douanevoorwerpen ](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/marketo-custom-objects/add-marketo-custom-object-fields) als user-defined voorwerpen toe om gespecialiseerde gegevens voorbij de standaardgebieden in Leads op te slaan, ondersteunend unieke bedrijfsbehoeften.
* AEM hebben alleen toegang tot aangepaste objecten als deze zijn gekoppeld aan de Lead-database

## Vereisten voor de integratie van Marketo Engage met formulieren

Hieronder vindt u de eerste vereisten voor de verbinding van Marketo Engage met AEM Forms:

* Een geldige Adobe Marketo Engage-licentie
* Een werkende instantie van Marketo Engage om [ identiteitskaart van de Cliënt en Geheime Cliënt ](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/additional-integrations/create-a-custom-service-for-use-with-rest-api) terug te winnen om een wolkenconfiguratie tot stand te brengen.

## Cloudserviceconfiguratie maken om AEM Forms (Adaptive Forms) te verbinden met Marketo Engage

![Workflow](/help/forms/assets/workflow-marketo-1.png)

>[!VIDEO](https://video.tv.adobe.com/v/3442865/engage-marketo-aem-forms-aem)

De configuratie van de Wolk verbindt uw instantie van de Experience Manager met de instantie van Adobe Marketo Engage. Voer de volgende stappen uit om een wolkenconfiguratie van het Marketo Engage tot stand te brengen:

1. Ga naar **Hulpmiddelen** > **Cloud Servicen** > **Marketo Engage**.

   ![ Marketo Engage ](/help/forms/assets/marketo-engage.png)

2. Open een omslag om de configuratie te ontvangen en **te klikken creeert**. Het **Create venster van de Configuratie van het Marketo Engage** verschijnt.

   >[!NOTE]
   >
   > U kunt ook [ omslag voor de configuraties van de wolkendienst ](/help/forms/configure-data-sources.md#configure-folder-for-cloud-service-configurations) vormen.

3. Specificeer de **Titel** van de configuratie en de geloofsbrieven om met de dienst te verbinden. U kunt de verificatiegegevens ophalen van het Adobe Marketo Engage-dashboard:
   * **identiteitskaart van de Cliënt** en **Geheime Cliënt** zijn beschikbaar in **Admin** > **Integratie** > **LaunchPoint** door de douanedienst te selecteren en **Details van de Mening te klikken**.
   * **Identiteit URL** is beschikbaar in **Admin** > **Integratie** > **Diensten van het Web** als **Identiteit** in de **REST API** sectie.

4. Klik **verbinden**.  Bij een geslaagde verbinding wordt het bericht `Authentication Successful` weergegeven.
5. Klik op **[!UICONTROL Create]** om de instellingen voor de cloudconfiguratie op te slaan.

![ Configuratie van de Wolk van het Marketo Engage ](/help/forms/assets/marketo-engage-cloud-configuration.png)

Nu kunt u de gemaakte cloudserviceconfiguratie gebruiken om de gegevensbron van het Marketo Engage aan te sluiten op een adaptief formulier.

## Volgende stap

U hebt de configuratie van de cloudservice gemaakt om Adobe Marketo Engage te integreren met AEM Forms. Nu kunt u integreren:
* [Nieuw adaptief formulier met Marketo Engage](/help/forms/integrate-adaptive-form-with-marketo-engage.md)
* [Bestaand adaptief formulier met Marketo Engage](/help/forms/use-marketo-engage-data-source-in-form.md)

## Verwante artikelen

{{af-submit-action}}

## Zie ook

{{marketo-engage-see-also}}
