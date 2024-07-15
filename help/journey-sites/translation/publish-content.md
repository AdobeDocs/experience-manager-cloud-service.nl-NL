---
title: Publish Vertaalde inhoud
description: Leer hoe u uw vertaalde inhoud publiceert en de vertalingen bijwerkt terwijl de inhoud wordt bijgewerkt.
index: true
hide: false
hidefromtoc: false
exl-id: 081167dd-da4c-48d2-a6d3-f95e873be3e9
solution: Experience Manager Sites
feature: Translation
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1326'
ht-degree: 0%

---

# Publish Vertaalde inhoud {#publish-content}

Leer hoe u uw vertaalde inhoud publiceert en de vertalingen bijwerkt terwijl de inhoud wordt bijgewerkt.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de de vertaalreis van AEM Sites, [ vertaal Inhoud, ](configure-connector.md) u leerde hoe te om AEM Vertaalprojecten te gebruiken om uw inhoud te vertalen. Nu moet u:

* Begrijp wat een vertaalproject is.
* U kunt nieuwe vertaalprojecten maken.
* Gebruik vertaalprojecten om uw inhoud te vertalen.

Nu uw eerste vertaling is voltooid, wordt in dit artikel de volgende stap gezet voor het publiceren van die inhoud en wat u moet doen om uw vertalingen bij te werken wanneer de onderliggende inhoud in de hoofdtaalwijziging verandert.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe te om inhoud in AEM te publiceren en hoe te om een voortdurende werkschema tot stand te brengen om uw vertalingen bijgewerkt te houden. Nadat u dit document hebt gelezen, moet u:

* Begrijp het auteur-publicatiemodel van AEM.
* Zorg dat u weet hoe u uw vertaalde inhoud publiceert.
* Een voortdurend updatemodel voor uw vertaalde inhoud kunnen implementeren.

## Auteur-Publish-model AEM {#author-publish}

Voordat u de inhoud publiceert, is het raadzaam om AEM schrijverpublicatiemodel te begrijpen. In vereenvoudigde termen verdeelt AEM gebruikers van het systeem in twee groepen.

1. Degenen die de inhoud en het systeem maken en beheren
1. Degenen die de inhoud van het systeem consumeren

AEM wordt daarom fysiek in twee gevallen gescheiden.

1. De **auteur** instantie is het systeem waar de inhoudsauteurs en de beheerders werken om inhoud tot stand te brengen en te beheren.
1. **publiceer** instantie is het systeem dat de inhoud aan de consumenten levert.

Nadat inhoud op de instantie van de auteur is gemaakt, moet deze naar de instantie publish worden overgedragen om de inhoud beschikbaar te maken voor consumptie. Het proces om van auteur over te brengen om te publiceren wordt genoemd **publicatie**.

## Uw vertaalde inhoud publiceren {#publishing}

Zodra u tevreden bent met de staat van uw vertaalde inhoud, moet het worden gepubliceerd zodat kan het worden en worden betreden en worden verbruikt. Deze taak valt gewoonlijk niet onder de verantwoordelijkheid van de vertaalspecialist, maar wordt hier beschreven om de volledige werkstroom te illustreren.

>[!NOTE]
>
>Wanneer de vertaling is voltooid, informeert de vertalingsspecialist de eigenaars van de inhoud over het feit dat de vertalingen klaar zijn voor publicatie. De eigenaars van de inhoud publiceren deze vervolgens.
>
>De volgende stappen worden verstrekt voor volledigheid.

De eenvoudigste manier om de vertalingen te publiceren is aan de projectomslag te navigeren.

```text
/content/<your-project>/
```

Onder dit pad hebt u submappen voor elke vertaaltaal en kunt u kiezen welke taal u wilt publiceren.

1. Ga naar **Navigatie** > **Plaatsen** > **Dossiers** en open de projectomslag.
1. Hier ziet u de hoofdmap van de taal en alle andere taalmappen. Selecteer de gelokaliseerde taal of talen die u wilt publiceren.
   ![ Uitgezochte taalomslag ](assets/select-language-folder.png)
1. Selecteer **Beheert Publicatie**.
1. In het **beheer Publicatie** venster, zorg ervoor dat **Publish** automatisch onder **Actie** wordt geselecteerd en dat **** nu onder **het Plannen** wordt geselecteerd. Selecteer **daarna**.
   ![ beheer publicatieopties ](assets/manage-publication-options.png)
1. In het volgende **leidt het venster van de Publicatie**, bevestig dat de juiste weg(en) wordt/worden geselecteerd. Selecteer **Publish**.
   ![ beheer publicatiewerkingsgebied ](assets/manage-publication-scope.png)
1. AEM bevestigt de publicatieactie met een pop-upbericht onder aan het scherm.
   ![ Van Middelen gepubliceerde banner ](assets/resources-published-message.png)

Uw vertaalde inhoud is nu gepubliceerd! Het kan nu worden betreden en worden verbruikt.

>[!TIP]
>
>U kunt meerdere items selecteren (dat wil zeggen meerdere taalmappen) wanneer u publiceert om meerdere vertalingen tegelijk te publiceren.

Er zijn extra opties wanneer het publiceren van uw inhoud, zoals het plannen van een publicatietijd, die buiten het werkingsgebied van deze reis zijn. Zie de [ Extra sectie van Middelen ](#additional-resources) aan het eind van het document voor meer informatie.

## Uw vertaalde inhoud bijwerken {#updating-translations}

Vertaling is zelden een eenmalige exercitie. Meestal blijven auteurs van inhoud uw inhoud toevoegen aan en wijzigen deze in de hoofdmap van de taal nadat de eerste vertaling is voltooid. Dit betekent dat u ook uw vertaalde inhoud moet bijwerken.

De specifieke projectvereisten bepalen hoe vaak u uw vertalingen moet bijwerken en welk besluitvormingsproces wordt gevolgd alvorens een update uit te voeren. Zodra u hebt besloten uw vertalingen bij te werken, is het proces in AEM zeer eenvoudig. Aangezien de eerste vertaling gebaseerd was op een vertaalproject, zijn ook updates mogelijk.

Het proces verschilt echter enigszins als u ervoor kiest om uw vertaalproject automatisch te maken of uw vertaalproject handmatig te maken.

### Een automatisch gemaakt vertaalproject bijwerken {#updating-automatic-project}

1. Navigeer aan **Navigatie** > **Assets** > **Dossiers**. Onthoud dat inhoud in AEM wordt opgeslagen onder `/content` .
1. Selecteer de taalwortel van uw project. In dit geval hebben we `/content/wknd/en` geselecteerd.
1. Selecteer de spoorselecteur en toon het **paneel van Verwijzingen**.
1. Selecteer **Exemplaren van de Taal**.
1. Controleer het **checkbox van de Kopieën van de Taal 0}.**
1. Breid de sectie **Exemplaren van de Taal van de Update** bij de bodem van het verwijzingenpaneel uit.
1. In de **drop-down lijst van het Project**, uitgezocht **voeg aan een bestaand Vertaalproject** toe.
1. In de **Bestaande drop-down lijst van het Project van de Vertaling**, selecteer het project dat voor de aanvankelijke vertaling wordt gecreeerd.
1. Selecteer **Update**.

![ voegt punten aan bestaand vertaalproject ](assets/add-to-existing-project.png) toe

De inhoud wordt toegevoegd aan het bestaande vertaalproject. Het vertaalproject weergeven:

1. Navigeer aan **Navigatie** > **Projecten**.
1. Selecteer het project dat u net hebt bijgewerkt.
1. Selecteer de taal of een van de talen die u hebt bijgewerkt.

U ziet dat er een nieuwe banenkaart aan het project is toegevoegd. In dit voorbeeld is een andere Spaanse vertaling toegevoegd.

![ Extra toegevoegde vertaalbaan ](assets/additional-translation-job.png)

U kunt zien dat de statistieken op de nieuwe kaart verschillend zijn. Dit komt omdat AEM herkent wat er is veranderd sinds de laatste vertaling en alleen de inhoud bevat die moet worden vertaald. Dit omvat het opnieuw vertalen van bijgewerkte inhoud en het voor het eerst vertalen van nieuwe inhoud.

Van dit punt, begint u [ en beheert uw vertaalbaan enkel aangezien u origineel deed.](translate-content.md#using-translation-project)

### Een handmatig gemaakt vertaalproject bijwerken {#updating-manual-project}

Als u een vertaling wilt bijwerken, kunt u een nieuwe taak toevoegen aan uw bestaande project die verantwoordelijk is voor het vertalen van de bijgewerkte inhoud.

1. Navigeer aan **Navigatie** > **Projecten**.
1. Selecteer het project dat u moet bijwerken.
1. Selecteer **toevoegen** knoop bij de bovenkant van het venster.
1. In **voeg het venster van de Tegel** toe, selecteer **VertaalBaan** en dan **voorlegt**.

   ![ voeg tegel ](assets/add-translation-job-tile.png) toe

1. Op de kaart van de nieuwe vertaalbaan, selecteer de chevron knoop bij de bovenkant van de kaart, en selecteer **Doel van de Update** om de doeltaal van de nieuwe baan te bepalen.

   ![ doel van de Update ](assets/update-target.png)

1. In de **Uitgezochte Taal van het Doel** dialoog, gebruik drop-down om de taal te selecteren en **Gedaane** te selecteren.

   ![ Uitgezochte doeltaal ](assets/select-target-language.png)

1. Als de doeltaal van uw nieuwe vertaaltaak is ingesteld, selecteert u de knop voor de weglatingsteken onder aan de taakkaart om de details van de taak weer te geven.
1. De taak is leeg wanneer deze voor het eerst wordt gemaakt. Voeg inhoud aan de baan toe door te tikken of te klikken **voeg** knoop toe en gebruikend wegbrowser [ zoals u voordien toen het creëren van het vertaalproject.](translate-content.md##manually-creating)

>[!TIP]
>
>De krachtige filters van de padbrowser kunnen ook weer nuttig zijn om alleen de inhoud te zoeken die is bijgewerkt.
>
>U kunt meer over wegbrowser in de [ extra middelensectie leren.](#additional-resources)

Van dit punt, begint u [ en beheert uw vertaalbaan enkel aangezien u origineel deed.](translate-content.md#using-translation-project)

## Einde van de reis? {#end-of-journey}

Gefeliciteerd! U hebt de AEM Sites vertaalreis voltooid! Nu moet u:

* U hebt een basiskennis AEM de functies voor contentbeheer.
* Begrijp AEM vertaaleigenschappen en hoe zij met uw plaatsinhoud verwant.
* Ga meteen door met het vertalen van uw eigen inhoud.

U bent nu klaar om uw eigen inhoud in AEM te vertalen. AEM is echter een krachtig hulpmiddel en er zijn veel aanvullende opties beschikbaar. Controle uit enkele extra middelen beschikbaar in de [ Extra sectie van Middelen ](#additional-resources) om meer over de eigenschappen te leren u in deze reis zag.

## Aanvullende bronnen {#additional-resources}

* [ het Leiden de Projecten van de Vertaling ](/help/sites-cloud/administering/translation/managing-projects.md) - leer de details van vertaalprojecten en extra eigenschappen zoals menselijke vertaalwerkschema&#39;s en meertalige projecten.
* [ Authoring concepten ](/help/sites-cloud/authoring/author-publish.md) - Leer meer over de auteur en publiceer het model van AEM. Dit document is gericht op het schrijven van pagina&#39;s in plaats van op inhoudfragmenten, maar de theorie blijft van toepassing.
* [ het Publiceren Pagina&#39;s ](/help/sites-cloud/authoring/sites-console/publishing-pages.md) - leer over de extra eigenschappen beschikbaar wanneer het publiceren van inhoud. Dit document is gericht op het schrijven van pagina&#39;s in plaats van op inhoudfragmenten, maar de theorie blijft van toepassing.
* [ Authoring Milieu en Hulpmiddelen ](/help/sites-cloud/authoring/path-selection.md#path-selection) - AEM verstrekt diverse mechanismen om uw inhoud met inbegrip van robuuste wegbrowser te organiseren en uit te geven.
