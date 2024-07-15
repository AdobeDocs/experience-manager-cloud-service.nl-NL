---
title: Productieprogramma's maken
description: Leer hoe u Cloud Manager kunt gebruiken om uw eigen productieprogramma te maken voor het hosten van live verkeer.
exl-id: 4ccefb80-de77-4998-8a9d-e68d29772bb4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 0%

---


# Productieprogramma&#39;s maken {#create-production-program}

Een productieprogramma is bedoeld voor een gebruiker die vertrouwd is met AEM en Cloud Manager en klaar is om te beginnen met het schrijven, bouwen en testen van code met als doel het op te stellen om levend verkeer te ontvangen.

Leer meer over programmatypes in het document [ Begrijpend Programma en de Types van Programma.](program-types.md)

## Een productieprogramma maken {#create}

Ga als volgt te werk om een productieprogramma te maken. Merk op dat afhankelijk van de rechten van uw organisatie, u [ extra opties ](#options) kunt zien wanneer het toevoegen van uw programma.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, tikt of klikt **Programma** in de hoogste juiste hoek van het scherm toevoegen.

   ![ manager die van de Wolk pagina ](assets/log-in.png) landt

1. Selecteer **Opstelling voor Productie** in de Create tovenaar van het Programma om een productieprogramma tot stand te brengen en een programmanaam te verstrekken.

   ![ Creërend programmatovenaar ](assets/create-production-program.png)

1. Naar keuze, kunt u een beeld aan het programma toevoegen door een beelddossier aan **te slepen en te laten vallen voeg een doel van het programmabeeld** toe of klikkend het om een beeld van een dossierbrowser te selecteren. Selecteer **verdergaan**.

1. Op het **Oplossingen &amp; toe:voegen-ons** lusje, selecteer de oplossingen om in het programma te omvatten.

   * Als u niet zeker weet of u een of meerdere programma&#39;s nodig hebt voor de verschillende beschikbare oplossingen, selecteert u de meest interessante oplossing. U kunt extra oplossingen activeren door [ het programma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) later uit te geven. Zie de [ Inleiding aan het document van de Programma&#39;s van de Productie ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) voor meer aanbevelingen van de programmaopstelling.
   * Er is minstens één oplossing vereist voor het maken van programma&#39;s.
   * Als u **[selecteerde laat Verbeterde Veiligheid](#security)** optie toe, wordt u toegestaan om slechts zo vele oplossingen te selecteren waarvoor de aanspraken van HIPAA beschikbaar zijn.

   ![ Uitgezochte oplossingen ](assets/setup-prod-select.png)

1. Klik de chevron vóór de oplossingsnamen om facultatieve toe:voegen-ons te openbaren zoals het selecteren van **Commerce** toe:voegen-op optie onder **Plaatsen**.

   ![ Uitgezochte toe:voegen-ons ](assets/setup-prod-commerce.png)

1. Met uw geselecteerde oplossingen en toe:voegen-ons, klik **verdergaan**.

1. Op **gaan-Levende Datum** lusje, ga de datum in u uw productieprogramma om levend te gaan.

   ![ bepalen geplande go-live datum ](assets/set-up-go-live.png)

   * Deze datum kan op elk moment worden bewerkt.
   * Deze datum is slechts voor informatief gebruik en brengt Go Live widget op het **pagina van het Overzicht van het Programma[** ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#program-overview) in werking om in-productverbindingen aan de beste praktijkdocumentatie van AEM as a Cloud Service op geschikte wijze te verstrekken om zich met uw reis te richten die in een succesvolle en vlotte Go Levende ervaring culmineert.

1. Klik **creëren**.

Uw programma is gemaakt door Cloud Manager en wordt weergegeven en geselecteerd op de bestemmingspagina.

![ het beheeroverzicht van de Wolk ](assets/navigate-cm.png)

## Aanvullende opties voor productieprogramma {#options}

Afhankelijk van de rechten waarover uw organisatie beschikt, hebt u mogelijk extra mogelijkheden wanneer u een productieprogramma maakt.

### Beveiliging {#security}

Als u de noodzakelijke rechten hebt, zal het **lusje van de Veiligheid** als eerste lusje in de **Opstelling voor de dialoog van de Productie** worden getoond.

Het **lusje van de Veiligheid** verstrekt de opties om **HIPAA** en/of **WAF-DDOS Bescherming** voor uw productieprogramma te activeren.

Adobe HIPAA-compatibel en Web Application Firewall (WAF) vereenvoudigt beveiliging op basis van cloud als onderdeel van een meerlagige aanpak ter bescherming tegen kwetsbaarheden.

* **HIPAA** - deze optie laat Adobe toe HIPPA-klaar oplossingsimplementatie.
   * [ Leer meer ](https://www.adobe.com/go/hipaa-ready) over HIPAA van de Adobe klaar oplossingsimplementatie.
   * HIPAA kan na het maken van het programma niet worden in- of uitgeschakeld.
* **WAF-DDOS Bescherming** - deze optie laat de firewall van de Webtoepassing via regels toe om uw toepassing te beschermen.
   * Zodra geactiveerd, kan de bescherming WAF-DDOS dan worden gevormd door opstelling a [ non-production pijpleiding.](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md)
   * Zie de regels van de Filter van het document [ Verkeer met inbegrip van de Regels van WAF ](/help/security/traffic-filter-rules-including-waf.md) leren hoe te om de regels van de verkeersfilter in uw bewaarplaats te beheren zodat worden zij behoorlijk opgesteld.

![ de opties van de Veiligheid ](assets/create-production-program-security.png)

### SLA {#sla}

Als u de noodzakelijke rechten hebt, zal het **SLA** lusje als tweede of derde lusje in de **Opstelling voor de dialoog van de Productie** worden getoond.

AEM Sites biedt een standaardovereenkomst voor 99,9% serviceniveau (SLA). De **optie van de Overeenkomst van het Niveau van de Dienst 0} 99.99% laat een minimumuptime van 99.99% voor uw productiemilieu&#39;s toe.**

99.99% SLA biedt voordelen met inbegrip van hogere beschikbaarheid en lagere latentie aan, en vereist een [ extra publiceer gebied ](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) om op het productiemilieu in het programma worden toegepast.

![ SLA opties ](assets/create-production-program-sla.png)

Zodra de [ vereisten ](#sla-requirements) voor het toelaten van 99.99% SLA worden voldaan, moet u a [ volledige stapelpijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) in werking stellen om het te activeren.

#### Eisen voor 99,99% SLA {#sla-requirements}

Naast de vereiste rechten heeft 99,99% SLA extra gebruiksvereisten.

* Zowel 99,99% SLA als extra rechten voor publicatiegebieden moeten beschikbaar zijn voor de organisatie op het moment dat zij 99,99% SLA toepast op het programma.
* Om 99.99% SLA op het programma toe te passen, zal Cloud Manager controleren om ervoor te zorgen dat een onverbruikte [ extra publiceer gebied ](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) recht ook beschikbaar is en op het programma kan worden toegepast.
* Als Cloud Manager bij het bewerken van een programma al een productieomgeving met minstens één extra publicatiegebied bevat, controleert alleen of een SLA-machtiging van 99,99% beschikbaar is.
* Opdat 99.99% SLA en het melden worden geactiveerd, moet het [ productie/stadium milieu ](/help/implementing/cloud-manager/manage-environments.md#adding-environments) zijn gecreeerd en minstens één extra publicatiegebied moet op het productie/stadium milieu zijn toegepast.
   * Als het gebruiken van [ geavanceerd voorzien van een netwerk, ](/help/security/configuring-advanced-networking.md) zorg ervoor om [ het Toevoegen van Veelvoudige Gebieden van Publish aan een Nieuw milieu ](/help/implementing/cloud-manager/manage-environments.md#adding-regions) document voor aanbevelingen te controleren zodat de connectiviteit in het geval van regionale mislukking wordt gehandhaafd.
* Er moet minstens één extra publicatiegebied in uw SLA-programma van 99,99% overblijven. Gebruikers mogen het laatste aanvullende publicatiegebied niet verwijderen uit uw SLA-programma van 99,99%.
* 99.99% SLA wordt gesteund voor productieprogramma&#39;s die de toegelaten oplossing van Plaatsen hebben.
* U moet a [ volledige stapelpijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) in werking stellen om (of, wanneer het uitgeven van een programma, deactief) 99.99% SLA te activeren.

## Toegang tot uw programma {#accessing}

1. Wanneer u uw programmacokaart op de landingspagina ziet, selecteer de elliptische knoop om de menuopties te bekijken beschikbaar aan u.

   ![ Overzicht van het Programma ](assets/program-overview.png)

1. Selecteer **Overzicht van het Programma** om aan de Cloud Manager **pagina van het Overzicht** te navigeren.

1. De belangrijkste vraag-aan-actie kaart op de overzichtspagina zal u door het creëren van een milieu, een niet productiepijplijn, en tenslotte een productiepijplijn begeleiden.

   ![ Overzicht van het Programma ](assets/set-up-prod5.png)

>[!TIP]
>
>Gelieve te zien het document [ Navigerend Cloud Manager UI ](/help/implementing/cloud-manager/navigation.md) voor details op hoe te Cloud Manager navigeren en het begrijpen van de **Mijn console van Programma&#39;s**.

>[!NOTE]
>
>In tegenstelling tot het programma van de a [ zandbak, ](introduction-sandbox-programs.md#auto-creation) zal een productieprogramma de gebruiker in de aangewezen rol van Cloud Manager vereisen om het project tot stand te brengen en een milieu door zelfbediening UI toe te voegen.
