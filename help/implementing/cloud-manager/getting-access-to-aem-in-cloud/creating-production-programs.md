---
title: Productieprogramma's maken
description: Leer hoe u Cloud Manager kunt gebruiken om uw eigen productieprogramma te maken voor het hosten van live verkeer.
exl-id: 4ccefb80-de77-4998-8a9d-e68d29772bb4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: cb9707e4f53e32ed6e5aec244b1ef2240fcf376c
workflow-type: tm+mt
source-wordcount: '1098'
ht-degree: 0%

---


# Productieprogramma&#39;s maken {#create-production-program}

Een productieprogramma is voor gebruikers vertrouwd met Adobe Experience Manager (AEM) en Cloud Manager, klaar om te schrijven, te bouwen, en code te testen, met het doel het op te stellen om levend verkeer te behandelen.

Leer meer over programmatypes in het document [ Begrijpend Programma en de Types van Programma ](program-types.md).

## Een productieprogramma maken {#create}

Afhankelijk van de rechten van uw organisatie, kunt u extra opties van het productieprogramma zien wanneer het toevoegen van uw programma.
Zie [ Extra opties van het productieprogramma ](#options).

**om een productieprogramma tot stand te brengen:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, dichtbij de hoger-juiste hoek, klik **Programma** toevoegen.

   ![ Cloud Manager landende pagina ](assets/log-in.png)

1. In *maak uw tovenaar van het Programma*, op het **Naam van het Programma** tekstgebied, typ de naam u voor het programma wilt.

1. Onder **Doelstelling van het Programma**, uitgezochte ![ pictogram van de Globe ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Globe_18_N.svg) **Opstelling voor productie**.

   ![ Creërend programmatovenaar ](assets/create-production-program.png)

1. (Optioneel) Voer in de rechterbenedenhoek van het dialoogvenster Wizard een van de volgende handelingen uit:

   * Sleep en laat vallen een beelddossier op het ![ pictogram van het Beeld ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Image_18_N.svg) **een doel van het programmabeeld** toevoegen.
   * Klik ![ pictogram van het Beeld ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Image_18_N.svg) **voeg een programmabeeld** toe, dan selecteer een beeld van een dossierbrowser.
   * Klik ![ pictogram van de Schrapping ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) om een beeld te verwijderen dat u toevoegde.

1. Klik **verdergaan**.

1. In de **Oplossingen &amp; toe:voegen-ons** lijstdoos, selecteer één of meerdere oplossingen om in het programma te omvatten.

   * Als u niet zeker weet of u een of meerdere programma&#39;s nodig hebt voor de verschillende beschikbare oplossingen, selecteert u de meest interessante oplossing. U kunt extra oplossingen activeren door [ het programma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md) later uit te geven. Zie de [ Inleiding aan het document van de Programma&#39;s van de Productie ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) voor meer aanbevelingen van de programmaopstelling.
   * Er is minstens één oplossing vereist voor het maken van programma&#39;s.
   * Selecteer **Edge levert de Diensten** voor een volledig beheerde oplossing CDN die digitale ervaringen optimaliseert. Zie [ Ongeveer gebruikend Edge Delivery Services om uw project van Cloud Manager te leveren ](#edge-overview)
   * Als u **[selecteerde laat Verbeterde Veiligheid](#security)** optie toe, kunt u slechts zo vele oplossingen selecteren waarvoor de aanspraken van HIPAA beschikbaar zijn.

     ![ Uitgezochte oplossingen ](/help/implementing/cloud-manager/assets/add-production-program-with-edge.png)

   * Klik {de grootte 300 van de Chevron van 0} pictogram ![&#128279;](https://spectrum.adobe.com/static/icons/ui_18/ChevronSize300.svg) links van een oplossingsnaam om het even welke facultatieve toe:voegen-ons, zoals **toe:voegen-op optie van Commerce** onder **Plaatsen** te openbaren.

   ![ Uitgezochte toe:voegen-ons ](assets/setup-prod-commerce.png)

1. Wanneer u wordt gedaan selecterend uw oplossingen en toe:voegen-ons, klik **verdergaan**.

1. Op **gaan-Levende Datum** lusje, ga de datum in die u van plan bent om uw productieprogramma te hebben Levend gaan.

   ![ bepalen geplande go-live datum ](assets/set-up-go-live.png)

   * U kunt deze datum op elk gewenst moment bewerken.
   * De datum dient informatiedoeleinden en brengt Go Live widget op het **pagina van het Overzicht van het Programma [&#128279;](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#program-overview) in werking.** Deze functionaliteit biedt tijdige productafhankelijke koppelingen naar de beste praktijken van AEM as a Cloud Service ter ondersteuning van een vloeiende Go Live-ervaring.

1. Klik **creëren**. Cloud Manager maakt uw programma en geeft het voor selectie weer op de bestemmingspagina.

   ![ het beheeroverzicht van de Wolk ](assets/navigate-cm.png)

## Aanvullende opties voor productieprogramma {#options}

Afhankelijk van de rechten waarover uw organisatie beschikt, hebt u mogelijk de volgende aanvullende opties beschikbaar wanneer u een productieprogramma maakt.

### Beveiliging {#security}

Als u de noodzakelijke rechten hebt, wordt het **lusje van de Veiligheid** getoond als eerste lusje in het **`Set up for production`** dialoogvakje.

![ de opties van de Veiligheid ](assets/create-production-program-security.png)

Het **lusje van de Veiligheid** verstrekt de opties om **HIPAA**, of **bescherming WAF-DDOS**, of allebei, voor uw productieprogramma te activeren.

Adobe HIPAA-compatibel en WAF-DDOS (Web Application Firewall - Distributed Denial of Service) vereenvoudigt beveiliging op basis van de cloud als onderdeel van een meerlagige aanpak ter bescherming tegen kwetsbaarheden.

* **HIPAA** - Deze optie laat de HIPA-Klaar oplossingsimplementatie van Adobe toe.
   * [ Leer meer ](https://www.adobe.com/trust/compliance/hipaa-ready.html) over Adobe HIPAA klaar oplossingsimplementatie.
   * HIPAA kan na het maken van het programma niet worden in- of uitgeschakeld.
* **bescherming WAF-DDOS** - Deze optie laat de Firewall van de Toepassing van het Web als regels toe om uw toepassing te beschermen.
   * Zodra geactiveerd, kan de bescherming WAF-DDOS dan worden gevormd door opstelling a [ niet productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).
   * Zie [ Regels van de Filter van het Verkeer met inbegrip van de Regels van WAF ](/help/security/traffic-filter-rules-including-waf.md) leren hoe te om de regels van de verkeersfilter in uw bewaarplaats te beheren zodat worden zij behoorlijk opgesteld.

### SLA {#sla}

Als u de noodzakelijke rechten hebt, wordt het **SLA** lusje getoond als tweede of derde lusje in het **`Set up for production`** dialoogvakje.

![ de opties van SLA ](assets/create-production-program-sla.png)

Sites en Forms bieden standaard 99,9% service level agreement (SLA). De **99.99% Service level agreement** optie garandeert een 99.99% minimumuptime voor uw productiemilieu&#39;s, of voor Plaatsen, Forms, Edge Delivery Services, of alle drie.

99,99% SLA biedt voordelen, zoals hogere beschikbaarheid en lagere latentie.

Voor Plaatsen en de programma&#39;s van Forms, vereist 99.99% SLA een [ extra publiceer gebied ](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) om op het productiemilieu in het programma worden toegepast. Wanneer de [ vereisten ](#sla-requirements) voor het toelaten van 99.99% SLA worden voldaan, moet u a [ volledige stapelpijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) in werking stellen om het te activeren.

Voor Edge Delivery Services, is er *geen* vereiste buiten het vormen van de 99.99% vergunning van SLA op het programma.

#### Eisen voor 99,99% SLA {#sla-requirements}

Naast de vereiste toeslagrechten worden met de 99,99% SLA for Sites- of Forms-programma&#39;s de volgende aanvullende eisen gesteld:

* De organisatie moet 99,99% SLA en aanvullende rechten voor publicatiegebieden beschikbaar hebben bij de toepassing van 99,99% SLA op het programma.
* Cloud Manager verifieert dat een ongebruikte [ extra publiceer gebied ](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) recht beschikbaar is alvorens 99.99% SLA op het programma toe te passen.
* Als Cloud Manager bij het bewerken van een programma al een productieomgeving met minstens één extra publicatiegebied bevat, controleert alleen of een SLA-machtiging van 99,99% beschikbaar is.
* Voor activering van 99.99% SLA en rapportering, moet het [ productie/stadium milieu ](/help/implementing/cloud-manager/manage-environments.md#adding-environments) zijn gecreeerd en minstens één extra publicatiegebied moet op het productie/stadium milieu zijn toegepast.
   * Als het gebruiken van [ geavanceerd voorzien van een netwerk ](/help/security/configuring-advanced-networking.md), zorg ervoor om [ het Toevoegen Meerdere publiceer Gebieden aan een Nieuw milieu ](/help/implementing/cloud-manager/manage-environments.md#adding-regions) document voor aanbevelingen te controleren zodat de connectiviteit wordt gehandhaafd als er regionale mislukking is.
* Uw 99,99% SLA-programma moet altijd minstens één extra publicatiegebied bevatten. Gebruikers mogen het laatste aanvullende publicatiegebied niet uit het programma verwijderen.
* Uw 99,99% SLA wordt ondersteund voor productieprogramma&#39;s waarvoor de oplossing Sites of Forms is ingeschakeld.
* Stel a [ volledige stapelpijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) in werking om te activeren of — wanneer het uitgeven van een programma — de 99.99% SLA deactiveren.

## Open uw programma {#accessing}

1. Wanneer u uw programmakaart op de het landen pagina ziet, klik ![ Meer pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) om de menuopties te bekijken beschikbaar aan u.

   ![ Overzicht van het Programma ](assets/program-overview.png)

1. Selecteer **Overzicht van het Programma** om aan de Cloud Manager **pagina van het Overzicht** te navigeren.

1. De belangrijkste vraag-aan-actie kaart op de overzichtspagina begeleidt u door het creëren van een milieu, een niet productiepijpleiding, en tenslotte een productiepijpleiding.

   ![ Overzicht van het Programma ](assets/set-up-prod5.png)

>[!TIP]
>
>Zie [ de UI van Cloud Manager ](/help/implementing/cloud-manager/navigation.md) voor details op navigeren Cloud Manager en het begrijpen van de **Mijn console van Programma&#39;s** navigeren.

>[!NOTE]
>
>In tegenstelling tot het programma van de a [ zandbak ](introduction-sandbox-programs.md#auto-creation), vereist een productieprogramma de gebruiker in de aangewezen rol van Cloud Manager om het project tot stand te brengen en een milieu door zelfbediening UI toe te voegen.


