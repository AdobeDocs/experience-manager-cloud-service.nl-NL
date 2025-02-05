---
title: Projecten
description: Met projecten kunt u bronnen groeperen in één entiteit waarvan de gemeenschappelijke, gedeelde omgeving het eenvoudig maakt om uw projecten te beheren
exl-id: c5f3331e-637f-4816-be83-faf2df59bd5f
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1253'
ht-degree: 7%

---

# Projecten {#projects}

Met projecten kunt u resources groeperen in één entiteit. Een gemeenschappelijke, gedeelde omgeving maakt het gemakkelijk om uw projecten te beheren. De soorten middelen u met een project kunt associëren worden bedoeld in AEM als Tegels. De tegels kunnen project en teaminformatie, activa, werkschema&#39;s, en andere soorten informatie omvatten, zoals die in detail in [ worden beschreven de Tegels van het Project ](#project-tiles).

>[!CAUTION]
>
>Voor gebruikers in projecten om andere gebruikers/groepen te zien terwijl het gebruiken van de functionaliteit van Projecten zoals het creëren van projecten, het creëren van taken/werkschema&#39;s, het zien van en het leiden van het team, die gebruikers moeten lees toegang op `/home/users` en `/home/groups` hebben. De gemakkelijkste manier om dit uit te voeren is de **project-gebruikers** groep te geven lees toegang tot `/home/users` en `/home/groups`.

Als gebruiker kunt u het volgende doen:

* Projecten maken
* Inhoud- en middelenmappen koppelen aan een project
* Projecten verwijderen
* Inhoudskoppelingen uit project verwijderen

Zie de volgende aanvullende onderwerpen:

* [Projecten beheren](/help/sites-cloud/authoring/projects/managing.md)
* [Werken met taken](/help/sites-cloud/authoring/projects/tasks.md)
* [Werken met projectworkflows](/help/sites-cloud/authoring/projects/workflows.md)

## Projectconsole {#projects-console}

De projectenconsole is waar u tot uw projecten binnen AEM toegang hebt en leidt.

![ de console van Projecten ](/help/sites-cloud/authoring/assets/projects-console.png)

* Selecteer **Chronologie** en dan een project om zijn chronologie te bekijken.
* Selecteer **Uitgezocht** om selectiewijze in te gaan.
* Klik **creëren** om projecten toe te voegen.
* **Knevel Actieve Projecten** laat u tussen alle projecten en slechts die schakelen die actief zijn.
* **toon de Mening van de Statistieken** laat u projectstatistieken betreffende taakvoltooiing zien.

## Projectblokken {#project-tiles}

Met Projecten, associeert u verschillende soorten informatie met uw projecten. Deze worden genoemd **Tegels**. Elk van de tegels en het soort informatie dat ze bevatten, wordt in deze sectie beschreven.

Aan uw project kunnen de volgende tegels zijn gekoppeld. Elk wordt beschreven in de volgende secties:

* Assets en asset collections
* Ervaringen
* Koppelingen
* Projectinformatie
* Team
* Openingspagina&#39;s
* E-mails
* Workflows
* Lanceringen
* Taken

### Assets {#assets}

In de **tegel van 0} Assets {, kunt u alle activa verzamelen die u voor een bepaald project gebruikt.**

![ de tegel van Assets ](/help/sites-cloud/authoring/assets/projects-assets-tile.png)

U uploadt elementen rechtstreeks in de tegel. Daarnaast kunt u Afbeeldingssets, Spin-sets of Gemengde mediasets maken als u over de invoegtoepassing Dynamic Media beschikt.

![ Reeks van het Beeld ](/help/sites-cloud/authoring/assets/projects-image-sets.png)

### Asset Collections {#asset-collections}

Gelijkaardig aan activa, kunt u [ activa inzamelingen ](/help/assets/manage-collections.md) direct aan uw project toevoegen. U definieert verzamelingen in Assets.

![ inzameling van Activa ](/help/sites-cloud/authoring/assets/projects-asset-collections.png)

Voeg een verzameling toe door op **Verzameling toevoegen** te klikken en de juiste verzameling in de lijst te selecteren.

### Ervaringen {#experiences}

De **tegel van de Ervaring 0} laat u een Mobiele app, een website, of een publicatie aan het project toevoegen.**

![ Ervaringen ](/help/sites-cloud/authoring/assets/project-experiences.png)

De pictogrammen geven aan welke ervaring wordt weergegeven: website, mobiele applicatie of een publicatie. Voeg ervaringen toe door neer te tikken of te klikken chevron en het tikken **voegt Ervaring** toe en het type van ervaring te selecteren.

![ voeg een ervaring toe ](/help/sites-cloud/authoring/assets/projects-add-experience.png)

Selecteer het pad voor de miniaturen en wijzig, indien van toepassing, de miniatuur voor de ervaring. De ervaringen worden gegroepeerd in de **tegel van Ervaring**.

### Koppelingen {#links}

Met de tegel Koppelingen kunt u externe koppelingen aan uw project koppelen.

![ Verbindingen ](/help/sites-cloud/authoring/assets/project-links.png)

U kunt de koppeling een naam geven die gemakkelijk herkenbaar is en de miniatuur wijzigen.

![ voeg verbinding ](/help/sites-cloud/authoring/assets/projects-add-link.png) toe

### Projectinfo {#project-info}

De tegel Projectinformatie bevat algemene informatie over het project, zoals een beschrijving, projectstatus (inactief of actief), een vervaldatum en leden. Bovendien kunt u een projectduimnagel toevoegen, die op de belangrijkste pagina van Projecten wordt getoond.

![ Info van het Project ](/help/sites-cloud/authoring/assets/project-info.png)

De leden van het team kunnen van deze tegel (of hebben hun rollen veranderd) en de tegel van het Team worden toegewezen en worden geschrapt.

![ voeg teamleden aan project ](/help/sites-cloud/authoring/assets/projects-add-team.png) toe

### Vertaaltaak {#translation-job}

In de tegel Vertaal-taak begint u een vertaling en ziet u ook de status van uw vertalingen. Aan opstelling uw vertaling, zie [ Creërend Vertaalprojecten ](/help/assets/translate-assets.md).

![ de baan van de Vertaling ](/help/sites-cloud/authoring/assets/projects-translation-job.png)

Klik de ellips bij de bodem van de **kaart van de Baan van de Vertaling** om de activa in het vertaalwerkschema te bekijken. In de lijst met vertaaltaken worden ook items voor metagegevens en tags van elementen weergegeven. Deze vermeldingen geven aan dat de metagegevens en tags voor de elementen ook worden vertaald.

![ het baandetail van de Vertaling ](/help/sites-cloud/authoring/assets/projects-translation-job-detail.png)

### Team {#team}

In deze tegel, kunt u de leden van het projectteam specificeren. Wanneer het uitgeven, kunt u de naam van het teamlid ingaan en de gebruikersrol toewijzen.

![ de tegel van het Team ](/help/sites-cloud/authoring/assets/projects-team-tile.png)

U kunt teamleden toevoegen en verwijderen uit het team. Bovendien kunt u de [ gebruikersrol ](#user-roles-in-a-project) uitgeven die aan het teamlid wordt toegewezen.

![ voeg team van lijst ](/help/sites-cloud/authoring/assets/projects-add-team-list.png) toe

### Workflows {#workflows}

U kunt uw project toewijzen om bepaalde workflows te volgen. Als om het even welke werkschema&#39;s lopen, hun statusvertoningen in de **tegel van Werkschema&#39;s** in Projecten.

![ Werkstromen ](/help/sites-cloud/authoring/assets/project-workflows.png)

U kunt uw project toewijzen om bepaalde workflows te volgen. Afhankelijk van welk project u kiest, hebt u verschillende beschikbare werkschema&#39;s.

Deze worden beschreven in [ Werkend met de Werkschema&#39;s van het Project ](/help/sites-cloud/authoring/projects/workflows.md).

### Lanceringen {#launches}

De tegel van Lanceringen toont om het even welke lanceringen die met het werkschema van de Lancering van het a [ Verzoek ](/help/sites-cloud/authoring/projects/workflows.md) zijn gevraagd.

![ Lanceringen ](/help/sites-cloud/authoring/assets/project-launches.png)

### Taken {#tasks}

Met Taken kunt u de status van projectgerelateerde taken, waaronder workflows, controleren. De taken worden behandeld in detail bij [ het Werken met Taken ](/help/sites-cloud/authoring/projects/tasks.md).

![ Taken ](/help/sites-cloud/authoring/assets/projects-tasks.png)

## Projectsjablonen {#project-templates}

AEM schepen met drie verschillende sjablonen uit de doos:

* Een eenvoudig project - een referentiemonster voor alle projecten die niet in andere categorieën passen (een &#39;catch-all&#39;-project). Het omvat drie basisrollen (Eigenaars, Editors, en Waarnemers) en vier werkschema&#39;s (de Goedkeuring van het Project, de Lancering van het Verzoek, de Pagina van het Aanbrengen van het Verzoek en E-mail van het Verzoek).
* Een mediaproject - een referentiemonsteringsproject voor aan media gerelateerde activiteiten. Het omvat verscheidene media verwante projectrollen (Fotografen, Editors, Copywriters, Ontwerpers, Eigenaars en Waarnemers). Het vraagt ook om een Copy-workflow om tekst aan te vragen en te bekijken.
* A [ vertaalproject ](/help/sites-cloud/administering/translation/overview.md) - een verwijzingssteekproef voor het beheren van vertaling verwante activiteiten. Het omvat drie basisrollen (Eigenaars, Editors, en Waarnemers). Het omvat twee werkschema&#39;s die in het gebruikersinterface van Workflows worden betreden.

Gebaseerd op het malplaatje u selecteert, hebt u verschillende opties beschikbaar aan u met name rond gebruikersrollen en werkschema&#39;s.

## Gebruikersrollen in een project {#user-roles-in-a-project}

De verschillende gebruikersrollen worden geplaatst in een malplaatje van het Project en om twee primaire redenen gebruikt:

1. Rechten. De gebruikersrollen vallen in één van de drie vermelde categorieën: Waarnemer, Redacteur, Eigenaar. Een fotograaf of copywriter heeft bijvoorbeeld dezelfde rechten als een Editor. De toestemmingen bepalen wat een gebruiker met inhoud in een project kan doen.
1. Workflows. De werkschema&#39;s bepalen wie taken in een project wordt toegewezen. De taken kunnen met een projectrol worden geassocieerd. U kunt bijvoorbeeld een taak toewijzen aan fotografen, zodat alle teamleden met de rol Fotograaf de taak krijgen.

Alle projecten steunen de volgende standaardrollen om u veiligheid en controletoestemmingen te laten beheren:

| Rol | Beschrijving | Machtigingen | Groepslidmaatschap |
|---|---|---|---|
| Waarnemer | Een gebruiker in deze rol kan projectdetails, met inbegrip van de projectstatus bekijken. | Alleen-lezen machtigingen voor een project | `workflow-users` groep |
| Editor | Een gebruiker met deze rol kan de inhoud van een project uploaden en bewerken. | Lees en schrijf toegang op een project, bijbehorende meta-gegevens, en verwante activa; voorrechten om een ontsproten lijst te uploaden, en activa te herzien en goed te keuren; schrijf toestemming op /etc/commerce; wijzig toestemming op een specifiek project | werkstroom-gebruikersgroep |
| Eigenaar | Een gebruiker met deze rol kan een project initiëren. Een eigenaar kan een project tot stand brengen, het werk in een project in werking stellen, en ook goedgekeurde activa naar de omslag van de Productie verplaatsen. Hoewel alle andere taken in het project ook door de eigenaar kunnen worden bekeken en worden uitgevoerd. | Schrijfmachtigingen op `/etc/commerce` | `dam-users` -groep (om een project te kunnen maken) projectbeheerders (om een project te kunnen maken en elementen te kunnen verplaatsen) |

>[!NOTE]
>
>Wanneer u het project creëert en gebruikers aan de verschillende rollen toevoegt, worden de groepen die aan het project gekoppeld zijn, automatisch gecreëerd om bijbehorende machtigingen te beheren. Bijvoorbeeld: een project met de naam Mijn project zou drie groepen hebben: **Mijn projecteigenaars**, **Mijn projecteditors**, **Mijn projectwaarnemers**. Als het project echter wordt verwijderd, worden deze groepen niet automatisch verwijderd. Een beheerder moet de groepen in **Hulpmiddelen** manueel schrappen > **Veiligheid** > **Groepen**.
