---
title: Sandbox-programma's - Cloud-service
description: Sandbox-programma's - Cloud-service
translation-type: tm+mt
source-git-commit: e7cad0cd67f04eac5627e72339ccb1c4f54cc8c8
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 0%

---


# Sandbox-programma&#39;s {#sandbox-programs}

## Inleiding {#introduction}

Een Sandbox-programma is een van de twee typen programma&#39;s die beschikbaar zijn in AEM Cloud Service, terwijl het andere een Regular-programma is.

Een zandbak wordt typisch gecreeerd om de doeleinden van opleiding, lopende demo&#39;s, enablement, of van het Bewijs van Concept (POC) te dienen. Zij zijn niet bedoeld om levend verkeer te vervoeren.

Sandbox-programma&#39;s omvatten Sites en Middelen en worden automatisch gevuld met een Git-vertakking die voorbeeldcode, een ontwikkelomgeving en een niet-productiepijplijn bevat.

Voor meer informatie over programmatypes, verwijs naar het [Begrip van Programma&#39;s en de Types](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html)van Programma.

### Attributen van Sandbox-programma&#39;s {#attributes-sandbox}

Sandbox-programma&#39;s hebben de volgende kenmerken:

1. **Programma maken:** Het maken van het Sandbox-programma omvat automatisch:
   * opstelling van project met steekproefcode en inhoud
   * totstandbrenging van een ontwikkelomgeving
   * de aanleg van een niet-productiepijpleiding die aan ontwikkelomgeving (hoofdtak die aan ontwikkelomgeving opstelt)

1. **Oplossingen:** Sandbox-programma&#39;s omvatten AEM-sites en -middelen.

1. **AEM-updates:** AEM-updates kunnen handmatig worden toegepast op omgevingen in een Sandbox-programma en worden niet automatisch geduwd.

1. **Sluimerstand:** De milieu&#39;s in een Sandbox programma worden automatisch gehiberd als geen activiteit voor een bepaalde periode wordt ontdekt. Gesamberde omgevingen kunnen handmatig worden gedehiberteerd.

### Sandboxprogramma&#39;s maken {#creating-sandbox-program}

Met een wizard voor het maken van programma&#39;s kunt u een Sandbox-programma maken.

Leer hoe te om een Programma van de Sandbox tot stand te brengen, verwijs naar het [Creëren van een Programma](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/creating-a-program.html#create-demo-program)Sandbox.

### Sandbox-omgevingen maken {#creating-sandbox-environments}

Sandbox-programma&#39;s worden automatisch in een ontwikkelomgeving geleverd op het moment dat het programma wordt gemaakt. De ontwikkelomgeving bevat standaard een auteur en een publicatielaag.

De productie-Stadium milieureeks kan manueel aan het Programma van Sandbox worden toegevoegd, wanneer de gebruiker aan opstelling een productiepijplijn klaar is.

Raadpleeg [Omgevingen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#adding-environments) toevoegen voor meer informatie over het handmatig maken van een omgeving.

### Sandbox-omgevingen verwijderen  {#deleting-sandbox-environments}

Gebruiker met de vereiste machtigingen kan een ontwikkelings- of productie-/werkgebiedomgeving of -sets verwijderen.

Als u een omgeving wilt verwijderen, raadpleegt u [Verwijderen van omgevingen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#deleting-environment) voor meer informatie.


## Sluiende en ontsmette zandbakomgevingen {#hibernating-introduction}

De milieu&#39;s van het Programma van de zandbak gaan een *hibernatiemodus* in als geen activiteit voor een bepaalde periode wordt ontdekt.

>[!NOTE]
>De sluimerstand is uniek voor Sandbox-programmaomgevingen. Reguliere programmeeromgevingen houden geen hiberatie in.

### Sluimerstand {#hibernation-introduction}

Sluimerstand kan automatisch of handmatig plaatsvinden. Het kan tot een paar minuten duren voor de milieu&#39;s van het Programma Sandbox om een *hibernatiemodus* in te gaan. De gegevens blijven behouden tijdens de hibernatie.

Sluimerstand wordt gecategoriseerd als:

* **De automatische** milieu&#39;s van het Programma van Sandbox worden automatisch gehiberneerd na acht uren van inactiviteit, betekenend dat noch de auteur noch de publicatieservices verzoek ontvangen.

* **Handmatig**: Als gebruiker kunt u handmatig een Sandbox-programmaomgeving herbergen, hoewel dit niet verplicht is, aangezien er na een bepaalde periode (acht uur) van inactiviteit automatisch sprake zal zijn van herberging.

#### Handmatige slaapstand gebruiken {#using-manual-hibernation}

U kunt uw Sandbox-programma handmatig op twee verschillende manieren via de Developer Console herbergen:

* Detailscherm omgeving
* Omgevingsscherm

Voer de onderstaande stappen uit om uw Sandbox-programmaomgevingen handmatig te hiberneren:

1. Navigeer naar de **Developer Console**.
Raadpleeg [Developer Console](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#accessing-developer-console) (Toegang tot ontwikkelaarsconsole) voor meer informatie over toegang tot de **ontwikkelaarsconsole** vanaf de **milieukeuren** .
1. Klik op Slaapstand, zoals in de onderstaande afbeelding wordt getoond:
1. Klik op **Slaapstand** om de stap te bevestigen
1. Wanneer de slaapstand is gelukt, ziet u het volgende scherm.

#### Een gedownloade omgeving openen {#accessing-hibernated-environment}

Wanneer de gebruiker een browser aanvraagt tegen de auteur of de publicatielaag van een gehiberneerde omgeving, komt de gebruiker een bestemmingspagina tegen waarin de gehiberneerde status van de omgeving wordt beschreven, zoals hieronder wordt geïllustreerd:

Een gebruiker met **Cloud Manager - de Rol** van de Ontwikkelaar kan op de knoop van de Console van de Ontwikkelaar klikken om tot de ontwikkelaarsconsole toegang te hebben en het milieu te ontruimen. Informatie over het instellen van rollen vindt u in de documentatie van Cloud Manager.

Als een gebruiker in een organisatie niet op de knop Developer Console kan klikken om naar de Developer Console te worden gebracht, is het waarschijnlijk dat hij of zij de rol &quot;Cloud Manager - Developer&quot; moet krijgen.


### De-hibernatie {#de-hibernation-introduction}

1. Navigeer naar de **Developer Console**.
Raadpleeg [Developer Console](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#accessing-developer-console) (Toegang tot ontwikkelaarsconsole) voor meer informatie over toegang tot de **ontwikkelaarsconsole** vanaf de **milieukeuren** .

   >[!IMPORTANT]
   >Toegang tot de ontwikkelaarsconsole wordt gedefinieerd door de rol **Ontwikkelaar in** Cloud Manager in de **beheerconsole**. Een gebruiker met een ontwikkelaarrol machtiging kan een Sandbox-programmaomgeving dehiberneren.

1. Klik op De- **hibernate**, zoals in onderstaande afbeelding wordt getoond:

   ![](assets/de-hibernation-img1.png)

1. Klik op **De Hibernate** om de stap te bevestigen.

   ![](assets/de-hibernation-img2.png)

1. U ontvangt het bericht dat het dehibernatieproces is gestart en u wordt bijgewerkt met de voortgang.

   ![](assets/de-hibernation-img3.png)

1. Zodra het proces voltooit, is het milieu van het Programma Sandbox opnieuw actief.

   ![](assets/de-hibernation-img4.png)


## AEM-updates voor Sandbox-omgevingen {#aem-updates-sandbox}


Raadpleeg de [AEM-versie-updates](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/deploying/overview.html#version-updates) voor meer informatie.

Een gebruiker kan AEM-updates handmatig toepassen op de omgevingen in een Sandbox-programma (zie onderstaande afbeelding). Dit kan worden gedaan wanneer de getoonde status **UPDATE BESCHIKBAAR** is.

De optie Bijwerken is beschikbaar in het vervolgkeuzemenu op de **milieucaart** . Deze optie is ook beschikbaar via de knop **Beheren** als u op **Details** van de **kaart voor omgevingen** klikt.

>[!NOTE]
>Een *niet-productiepijpleiding* die aan het ontwikkelmilieu van belang opstelt moet worden gevormd om een handupdate pijpleiding in werking te stellen.

>[!NOTE]
>Er moet een *productiepijpleiding* worden geconfigureerd om een handmatige updatepijpleiding naar Production+Stage-omgeving te laten starten.

>[!NOTE]
>Handmatige update naar *Productie* - of *werkgebiedomgeving* werkt automatisch de andere bij. De omgeving Production+Stage moet zich op dezelfde AEM-versie bevinden.





