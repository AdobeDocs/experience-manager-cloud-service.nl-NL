---
title: Sandbox-programma's - Cloud-service
description: Sandbox-programma's - Cloud-service
translation-type: tm+mt
source-git-commit: eb874176c71d7f3d03d953f7bae4cb3db2ffb3b9
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---


# Sandbox-programma&#39;s {#sandbox-programs}

## Inleiding {#introduction}

Een Sandbox-programma is een van de twee typen programma&#39;s die beschikbaar zijn in AEM Cloud Service, terwijl het andere een Regular-programma is.

Een zandbak wordt typisch gecreeerd om de doeleinden van opleiding, lopende demo&#39;s, enablement, of POCs te dienen. Zij zijn niet bedoeld om levend verkeer te vervoeren.

Sandbox-programma&#39;s omvatten Sites en Middelen en worden automatisch gevuld met een Git-vertakking die voorbeeldcode, een ontwikkelomgeving en een niet-productiepijplijn bevat.

Voor meer informatie over programmatypes, verwijs naar het [Begrip van Programma&#39;s en de Types](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html)van Programma.

### Attributen van Sandbox-programma&#39;s {#attributes-sandbox}

Sandbox-programma&#39;s hebben de volgende kenmerken:

1. **Programma maken:** Het maken van het Sandbox-programma omvat automatisch:
   * opstelling van project met steekproefcode en inhoud
   * totstandbrenging van een ontwikkelomgeving
   * de aanleg van een niet-productiepijpleiding die aan ontwikkelomgeving (hoofdtak die aan het milieu van de Ontwikkeling opstelt)

1. **Oplossingen inbegrepen:** Sandbox-programma&#39;s bevatten sites en elementen.

1. **AEM-updates:** AEM-updates kunnen handmatig worden toegepast op omgevingen in een Sandbox-programma en worden niet automatisch geduwd.

1. **Sluimerstand:** De omgevingen in een Sandbox-programma worden automatisch gedempt als er gedurende een bepaalde periode geen activiteit wordt gedetecteerd. Gesamberde omgevingen kunnen handmatig worden gedehiberteerd.

### Sandboxprogramma&#39;s maken {#creating-sandbox-program}

Een wizard voor het maken van programma&#39;s vraagt de gebruiker om gegevens te verzenden.

Raadpleeg Sandboxprogramma&#39;s [maken voor informatie over het maken van een sandboxprogramma](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/creating-a-program.html#create-demo-program).

### Sandbox-omgevingen maken {#creating-sandbox-environments}

Sandbox-programma&#39;s worden automatisch in een ontwikkelomgeving geplaatst op het moment dat het programma wordt gemaakt. De ontwikkelomgeving wordt standaard geleverd met een auteur en een publicatielaag.

De productie-Stadium milieureeks kan manueel aan het Sandbox programma worden toegevoegd, wanneer de gebruiker aan opstelling een productiepijplijn klaar is.

Raadpleeg [Omgevingen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#adding-environments)toevoegen voor informatie over het handmatig maken van een omgeving.

### Sandbox-omgevingen verwijderen  {#deleting-sandbox-environments}

Gebruikers met de vereiste machtigingen kunnen een ontwikkelings- of productie-/werkgebiedomgeving of -sets verwijderen.

Raadpleeg [Verwijderen van omgevingen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#deleting-environment)voor informatie over het verwijderen van een omgeving.


## Sluiende en ontsmette zandbakomgevingen {#hibernating-introduction}

Sandbox-programmaomgevingen worden na een periode van inactiviteit in een *hibernatiemodus* geplaatst.

>[!NOTE]
>Hibernatie is uniek in sandboxprogrammaomgevingen. Normale programmaomgevingen worden niet gehiberd.

### Sluimerstand {#hibernation-introduction}

Sluimerstand kan automatisch of handmatig plaatsvinden. Het kan een paar minuten duren voordat een omgeving wordt gehiberd. De gegevens blijven behouden tijdens de hibernatie.

Sluimerstand wordt gecategoriseerd als:

* **Automatische** Sandbox-programmaomgevingen worden na acht uur inactiviteit automatisch gehiberd. Dit betekent dat noch de auteur-, noch de publicatieservices een aanvraag ontvangen.

* **Handmatig**: Klanten kunnen een omgeving van een sandboxprogramma handmatig herbergen, maar dit is niet verplicht, aangezien de situatie na een periode van inactiviteit automatisch zal worden gewijzigd.

#### Handmatige slaapstand gebruiken {#using-manual-hibernation}


De handmatige hibernatie kan van één van beide schermen in de ontwikkelaarsconsole worden verwezenlijkt.

Voer de onderstaande stappen uit om uw programmaomgevingen handmatig te hiberneren:

1. Navigeer naar de Developer Console.
1. Klik op Sluimerstand
1. Klik op Slaapstand om te bevestigen.
1. Wanneer de slaapstand is gelukt, ziet u het volgende scherm.
1. Op het scherm van milieulijsten, dat hieronder wordt geïllustreerd en toegankelijk door de verbinding van Milieu van het het gedetailleerde scherm van het milieu te klikken, kan de knoop van de Sluimerstand in de rij van het voorgenomen milieu worden geklikt. Er verschijnt dan een bevestigingsscherm.

### De-hibernatie {#de-hibernation-introduction}

>[!IMPORTANT]
>De toegang tot de ontwikkelaarsconsole wordt gedefinieerd door de functie ‘Cloud Manager - Developer Role’ in de beheerconsole. Met die toestemming, kan een gebruiker een milieu ontberen.

### Een gedownloade omgeving openen {#accessing-hibernated-environment}

Wanneer de gebruiker een browser aanvraagt tegen de auteur of de publicatielaag van een gehiberneerde omgeving, komt de gebruiker een bestemmingspagina tegen waarin de gehiberneerde status van de omgeving wordt beschreven, zoals hieronder wordt geïllustreerd:

Een gebruiker met de functie ‘Cloud Manager - Developer Role’ kan op de knop Developer Console klikken om toegang te krijgen tot de ontwikkelaarsconsole en de omgeving te dehiberneren. Informatie over het instellen van rollen vindt u in de documentatie van Cloud Manager.

Als een gebruiker in een organisatie niet op de knop Developer Console kan klikken om naar de Developer Console te worden gebracht, is het waarschijnlijk dat hij of zij de rol &quot;Cloud Manager - Developer&quot; moet krijgen.




## AEM-updates voor Sandbox-omgevingen {#aem-updates-sandbox}


Raadpleeg de [AEM-versie-updates](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#version-updates).

De gebruiker kan AEM-updates handmatig toepassen op de omgevingen in een Sandbox-programma (zie onderstaande afbeelding). Dit kan worden gedaan wanneer de getoonde status BESCHIKBAAR UPDATE is. De optie Bijwerken is beschikbaar in het vervolgkeuzemenu op de Environmental Card. U kunt deze optie ook selecteren in het menu Beheren in het scherm OMGEVINGEN.

>[!NOTE]
>Een niet-productiepijpleiding die aan de ontwikkelomgeving van belang opstelt moet worden gevormd om een handupdate pijpleiding in werking te stellen.

>[!NOTE]
>Een productiepijpleiding moet worden gevormd om een handupdate pijpleiding aan Productie+Stage milieu te beginnen wordt geplaatst.

>[!NOTE]
>Handmatige update naar de productieomgeving of de werkgebiedomgeving werkt automatisch de andere bij. De omgeving Production+Stage moet zich op dezelfde AEM-versie bevinden.





