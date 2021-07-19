---
title: Vertaalde inhoud publiceren
description: Leer hoe u gelokaliseerde inhoud publiceert.
source-git-commit: 3ab886361dc01c943bd00025695d34a218b1aa41
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# Vertaalde inhoud publiceren {#publish-content}

Leer hoe u gelokaliseerde inhoud publiceert.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM hoofdloze lokalisatietraject hebt u [Inhoud vertalen,](configure-connector.md) geleerd hoe u AEM vertaalprojecten kunt gebruiken om uw inhoud zonder kop te vertalen. Nu moet u:

* Begrijp wat een vertaalproject is.
* Nieuwe vertaalprojecten kunnen maken.
* Gebruik vertaalprojecten om uw inhoud zonder kop te vertalen.

Nu uw eerste vertaling is voltooid, wordt in dit artikel de volgende stap gezet voor het publiceren van die inhoud en wat u moet doen om uw vertalingen bij te werken wanneer de onderliggende taalhoofdinhoud verandert.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u inhoud zonder kop in AEM kunt publiceren en hoe u een continue workflow kunt maken om uw vertalingen up-to-date te houden. Nadat u dit document hebt gelezen, moet u:

* Begrijp het auteur-publicatiemodel van AEM.
* Zorg dat u weet hoe u uw vertaalde inhoud publiceert.
* Een voortdurend updatemodel voor uw vertaalde inhoud kunnen implementeren.

## Auteur-publicatiemodel AEM {#author-publish}

Voordat u de inhoud publiceert, is het verstandig om AEM publicatiemodel te begrijpen. In zijn eenvoudigste termen verdeelt AEM gebruikers van het systeem in twee groepen.

1. Degenen die de inhoud en het systeem maken en beheren
1. Degenen die de inhoud van het systeem consumeren.

AEM wordt daarom fysiek in twee gevallen gescheiden.

1. De **auteur**-instantie is het systeem waarin auteurs en beheerders van inhoud werken aan het maken en beheren van inhoud.
1. De **publish** instantie is het systeem dat de inhoud aan de consumenten levert.

Nadat inhoud op de instantie van de auteur is gemaakt, moet deze naar de instantie publish worden overgedragen om de inhoud beschikbaar te maken voor consumptie. Het proces om van auteur over te brengen om te publiceren wordt genoemd **publicatie**.

## Uw vertaalde inhoud publiceren {#publishing}

Als u tevreden bent met de status van uw vertaalde inhoud, kunt u deze publiceren zodat services zonder kop de inhoud kunnen consumeren. De gemakkelijkste manier om dit te doen is aan de omslag van projectactiva te navigeren.

```text
/content/dam/<your-project>/
```

Onder dit pad hebt u submappen voor elke vertaaltaal en kunt u kiezen welke taal u wilt publiceren.

1. Ga naar **Navigation** -> **Middelen** -> **Bestanden** en open de projectmap.
1. Hier ziet u de hoofdmap van de taal en alle andere taalmappen. Selecteer de gelokaliseerde taal of talen die u wilt publiceren.
   ![Taalmap selecteren](assets/select-language-folder.png)
1. Tik of klik op **Publicatie beheren**.
1. Controleer in het venster **Publicatie beheren** of **Publiceren** automatisch is geselecteerd onder **Action** en of **Now** is geselecteerd onder **Scheduling**. Tik of klik op **Volgende**.
   ![Publicatieopties beheren](assets/manage-publication-options.png)
1. Bevestig in het volgende venster **Publicatie beheren** dat het juiste pad of de juiste paden is/zijn geselecteerd. Tik of klik op **Publiceren**.
   ![Publicatiebereik beheren](assets/manage-publication-scope.png)
1. AEM bevestigt de publicatieactie met een pop-upbericht onder aan het scherm.
   ![Bronnen gepubliceerde banner](assets/resources-published-message.png)

De gelokaliseerde inhoud zonder kop is nu gepubliceerd! Het kan nu door uw headless diensten worden betreden en worden verbruikt.

>[!TIP]
>
>U kunt bij het publiceren meerdere items selecteren (dat wil zeggen meerdere taalmappen) om meerdere lokalisaties tegelijk te publiceren.

Er zijn extra opties wanneer het publiceren van uw inhoud zoals het plannen van een publicatietijd die voorbij het werkingsgebied van deze reis zijn. Zie de sectie [Aanvullende bronnen](#additional-resources) aan het einde van het document voor meer informatie.

## Uw vertaalde inhoud bijwerken {#updating-translations}

Lokalisatie en vertaling is zelden een eenmalige exercitie. Meestal blijven auteurs van inhoud uw inhoud toevoegen aan en wijzigen deze in de hoofdmap van de taal nadat de eerste lokalisatie is voltooid. Dit betekent dat u ook uw vertaalde inhoud moet bijwerken.

Met specifieke projectvereisten wordt bepaald hoe vaak u uw vertalingen moet bijwerken en welk besluitvormingsproces moet worden gevolgd voordat u een update uitvoert. Zodra u hebt besloten uw vertalingen bij te werken, is het proces in AEM zeer eenvoudig. Aangezien de eerste vertaling gebaseerd was op een vertaalproject, zijn ook updates mogelijk.

1. Navigeer naar **Navigation** -> **Middelen** -> **Bestanden**. Onthoud dat inhoud zonder kop in AEM wordt opgeslagen als elementen die Content Fragments worden genoemd.
1. Selecteer de taalwortel van uw project. In dit geval hebben we `/content/dam/wknd/en` geselecteerd.
1. Tik op de spoorkiezer of klik op deze en toon het venster **References**.
1. Tik of klik op **Taalkopieën**.
1. Schakel het selectievakje **Taalkopieën** in.
1. Vouw de sectie **Taalkopieën bijwerken** onder in het venster Referenties uit.
1. Selecteer **Toevoegen aan een bestaand vertaalproject** in het vervolgkeuzemenu **Project**.
1. Selecteer in het vervolgkeuzemenu **Bestaand vertaalproject** het project dat u voor de eerste vertaling hebt gemaakt.
1. Tik of klik op **Start**.

![Items toevoegen aan bestaand vertaalproject](assets/add-to-existing-project.png)

De inhoud wordt toegevoegd aan het bestaande vertaalproject. Het vertaalproject weergeven:

1. Navigeer naar **Navigation** -&amp; **Projecten**.
1. Tik of klik op het project dat u zojuist hebt bijgewerkt.
1. Tik of klik op de taal of een van de talen die u hebt bijgewerkt.

U zult zien dat een nieuwe banenkaart aan het project werd toegevoegd. In dit voorbeeld is een andere Spaanse vertaling toegevoegd.

![Extra vertaalbaan toegevoegd](assets/additional-translation-job.png)

U zult zien dat de statistieken op de nieuwe kaart (aantal activa en inhoudsfragmenten) verschillend zijn. Dit komt omdat AEM herkent wat er is gewijzigd sinds de laatste vertaling en alleen nieuwe inhoud bevat die moet worden vertaald (zowel opnieuw vertaalde bijgewerkte inhoud als nieuwe inhoud).

Vanaf dit punt kunt u uw vertaaltaak net als het origineel starten en beheren.](translate-content.md#using-translation-project)[

## Einde van de reis? {#end-of-journey}

Gefeliciteerd! U hebt de reis zonder kop van lokalisatie voltooid! Nu moet u:

* Heb een overzicht van wat de levering van inhoud zonder kop is.
* U hebt een basiskennis AEM functies zonder kop.
* Begrijp AEM lokalisatiefuncties en hoe deze gerelateerd zijn aan inhoud zonder kop.
* De mogelijkheid hebben om uw eigen inhoud zonder kop te lokaliseren.

U kunt nu uw eigen inhoud zonder kop lokaliseren in AEM. AEM is echter een krachtig hulpmiddel en er zijn veel aanvullende opties beschikbaar. Bekijk een aantal aanvullende bronnen in de volgende sectie voor meer informatie over de functies die u tijdens deze reis hebt gezien.

## Aanvullende bronnen {#additional-resources}

* [Vertaalprojecten](/help/sites-cloud/administering/translation/managing-projects.md)  beheren - Meer informatie over vertaalprojecten en aanvullende functies, zoals workflows voor menselijke vertaling en meertalige projecten.
* [Ontwerpconcepten](/help/sites-cloud/authoring/getting-started/concepts.md)  - Leer meer over de auteur en publiceer het model van AEM. Dit document is gericht op het schrijven van pagina&#39;s in plaats van op inhoudfragmenten, maar de theorie blijft van toepassing.
* [Pagina&#39;s](/help/sites-cloud/authoring/fundamentals/publishing-pages.md)  publiceren - Meer informatie over de extra functies die beschikbaar zijn wanneer u inhoud publiceert. Dit document is gericht op het schrijven van pagina&#39;s in plaats van op inhoudfragmenten, maar de theorie blijft van toepassing.
