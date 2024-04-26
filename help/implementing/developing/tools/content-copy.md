---
title: Het gereedschap Inhoud kopiëren
description: Met het hulpprogramma voor het kopiëren van inhoud kunnen gebruikers op verzoek muterende inhoud uit hun productieomgeving kopiëren op AEM as a Cloud Service naar lagere omgevingen voor testdoeleinden.
exl-id: 5883e4bc-9861-498e-bd35-32ff03d901cc
source-git-commit: a0f80a363cb47be9e3d8f7fa96ea3068eb077d42
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 0%

---

# Het gereedschap Inhoud kopiëren {#content-copy}

Met het hulpprogramma voor het kopiëren van inhoud kunnen gebruikers op verzoek muterende inhoud uit hun productieomgeving kopiëren op AEM as a Cloud Service naar lagere omgevingen voor testdoeleinden.

## Inleiding {#introduction}

De huidige, echte gegevens zijn waardevol voor het testen, de bevestiging, en de gebruiker-aanvaarding doeleinden. Met het gereedschap Inhoud kopiëren kunt u inhoud kopiëren van een productie AEM een as a Cloud Service omgeving naar een testomgeving, ontwikkeling of [Rapid Development Environment (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) omgeving voor dergelijke tests.

De inhoud die moet worden gekopieerd, wordt gedefinieerd door een inhoudsset. Een inhoudenset bestaat uit een lijst met JCR-paden die de veranderbare inhoud bevatten die van een ontwerpomgeving van een bron naar een ontwerpomgeving van een doel binnen hetzelfde Cloud Manager-programma moet worden gekopieerd. De volgende paden zijn toegestaan in een inhoudsset.

```text
/content
/conf/**/settings/wcm
/conf/**/settings/dam/cfm/models
/conf/**/settings/graphql/persistentQueries
/etc/clientlibs/fd/themes
```

Wanneer het kopiëren van inhoud, is het bronmilieu de bron van waarheid.

* Als de inhoud in de bestemmingsmilieu is gewijzigd, wordt het beschreven door inhoud in de bron, als de wegen het zelfde zijn.
* Als de paden verschillend zijn, wordt de inhoud van de bron samengevoegd met de inhoud in de bestemming.

## Machtigingen {#permissions}

Als u het gereedschap Inhoud kopiëren wilt gebruiken, zijn bepaalde machtigingen vereist in zowel de bronomgeving als de doelomgeving.

| Functie Inhoud kopiëren | Beheerdersgroep AEM | Implementatiebeheerfunctie |
|---|---|---|
| Maken en wijzigen [inhoudssets](#create-content-set) | Niet vereist | Vereist |
| Start of annuleer de [kopiëren van inhoud, proces](#copy-content) | Vereist | Vereist |

Zie voor meer informatie over machtigingen en hoe u deze kunt instellen [as a Cloud Service teams en productprofielen AEM](/help/onboarding/aem-cs-team-product-profiles.md).

## Een inhoudsset maken {#create-content-set}

Voordat inhoud kan worden gekopieerd, moet een inhoudsset zijn gedefinieerd. Nadat deze is gedefinieerd, kunnen inhoudssets opnieuw worden gebruikt om inhoud te kopiëren. Voer de volgende stappen uit, zodat u een inhoudsset kunt maken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Navigeer met het zijnavigatievenster naar het **Inhoudssets** van de **Overzicht** pagina.

1. Klik rechtsboven in het scherm op **Inhoudsset toevoegen**.

   ![Inhoudssets](assets/content-sets.png)

1. Op de **Details** Geef een naam en beschrijving op voor de inhoudenset en selecteer **Doorgaan**.

   ![Details van inhoudsset](assets/add-content-set-details.png)

1. Op de **Inhoudspaden** van de wizard, geeft u de paden op van de inhoud die u wilt wijzigen.

   1. Voer het pad in het dialoogvenster **Inclusief pad toevoegen** veld.
   1. Klikken **Pad toevoegen** om het pad aan de inhoudenset toe te voegen.
   1. Klikken **Pad toevoegen** nogmaals indien nodig.
      * Er zijn maximaal 50 paden toegestaan.

   ![Paden toevoegen aan inhoudsset](assets/add-content-set-paths.png)

1. Als u de inhoudenset moet verfijnen of beperken, kunnen subpaden worden uitgesloten.

   1. Klik in de lijst met opgenomen paden op **Subpaden uitsluiten toevoegen** naast het pad dat u wilt beperken.
   1. Voer het subpad in dat u onder het geselecteerde pad wilt uitsluiten.
   1. Selecteren **Pad uitsluiten**.
   1. Selecteren **Subpaden uitsluiten toevoegen** nogmaals om extra paden toe te voegen om deze uit te sluiten.
      * Uitgesloten paden moeten relatief zijn ten opzichte van het ingesloten pad.
      * Het aantal uitgesloten paden is niet beperkt.

   ![Paden uitsluiten](assets/add-content-set-paths-excluded.png)

1. U kunt de opgegeven paden desgewenst bewerken.

   1. Klik op de X naast de uitgesloten subpaden, zodat u deze kunt verwijderen.
   1. Klik op de knop Ovaal naast paden zodat u deze kunt tonen **Bewerken** en **Verwijderen** opties.

   ![Padlijst bewerken](assets/add-content-set-excluded-paths.png)

1. Selecteren **Maken** om de inhoudenset te maken.

De inhoudenset kan nu worden gebruikt om inhoud tussen omgevingen te kopiëren.

## Een inhoudsset bewerken {#edit-content-set}

Voer vergelijkbare stappen uit als bij het maken van een stap Inhoud. In plaats van te klikken **Inhoudsset toevoegen**, selecteert u een bestaande set in de console en selecteert u **Bewerken** in het ovaalmenu.

![Inhoudsset bewerken](assets/edit-content-set.png)

Wanneer u de inhoudenset bewerkt, kunt u de geconfigureerde paden uitbreiden om de uitgesloten subpaden zichtbaar te maken.

## Inhoud kopiëren {#copy-content}

Nadat u een inhoudsset hebt gemaakt, kunt u deze gebruiken om inhoud te kopiëren. Voer de volgende stappen uit om inhoud te kopiëren.

>[!NOTE]
> Gebruik Inhoud kopiëren niet in een omgeving als een [inhoudsoverdracht](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md) de bewerking wordt uitgevoerd in die omgeving.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Omgevingen** van het scherm **Overzicht** pagina.

1. Ga naar de **Inhoudssets** pagina van de **Omgevingen** scherm.

1. Selecteer een inhoudsset in de console en selecteer **Inhoud kopiëren** in het ovaalmenu.

   ![Inhoud kopiëren](assets/copy-content.png)

   >[!NOTE]
   >
   >Een omgeving kan niet selecteerbaar zijn als:
   >
   >* De gebruiker beschikt niet over de juiste machtigingen.
   >* Het milieu heeft een lopende pijpleiding of een verrichting van de exemplaarinhoud lopend.
   >* Het milieu is aan het huren of opstarten.

1. In de **Inhoud kopiëren** geeft u de bron en de bestemming op voor de actie Kopiëren van inhoud.

   ![Inhoud kopiëren](assets/copying-content.png)

   * Inhoud kan alleen worden gekopieerd van een hogere omgeving naar een lagere omgeving of tussen ontwikkelings-/RDE-omgevingen waarin de hiërarchie van omgevingen als volgt is (van hoogste naar laagste):
      * Productie
      * Staging
      * Ontwikkeling/RDE

1. Indien nodig kunt u ook **Lijsten met toegangsbeheer opnemen** in uw kopieerproces.

1. Selecteren **Kopiëren**.

Het kopieerproces wordt gestart. De status van het kopieerproces wordt weerspiegeld in de console voor de geselecteerde inhoudenset.

## Activiteit voor kopiëren van inhoud {#copy-activity}

U kunt de status van uw kopieerprocessen in de **Inhoudsactiviteit kopiëren** pagina.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Omgevingen** van het scherm **Overzicht** pagina.

1. Ga naar de **Inhoudsactiviteit kopiëren** pagina van de **Omgevingen** scherm.

![Activiteit voor kopiëren van inhoud](assets/copy-content-activity.png)

### Statussen van inhoud kopiëren {#statuses}

Wanneer u begint inhoud te kopiëren, kan het proces een van de volgende statussen hebben.

| Status | Beschrijving |
|---|---|
| In uitvoering | De bewerking voor het kopiëren van inhoud is aan de gang |
| Mislukt | Kopiëren van inhoud is mislukt |
| Voltooid | Kopie van inhoud voltooid |
| Geannuleerd | Gebruiker annuleert een bewerking voor het kopiëren van inhoud nadat deze is gestart |

### Een kopieerproces annuleren {#canceling}

Als u een bewerking voor het kopiëren van inhoud moet afbreken nadat u deze hebt gestart, kunt u deze desgewenst annuleren.

Om dit te doen, **Inhoudsactiviteit kopiëren** pagina, selecteert u de **Annuleren** actie van het elliptische menu van het exemplaarproces u eerder begon.

![Kopie van inhoud annuleren](assets/content-copy-cancel.png)

>[!NOTE]
>
>Wanneer u een bewerking voor het kopiëren van inhoud annuleert, kan dit resulteren in een gedeeltelijke kopie van de inhoud in de doelomgeving. Deze situatie kan het bestemmingsmilieu in een onbruikbaar geval verlaten.
>
>Als uw omgeving zich in een dergelijke toestand bevindt als gevolg van annulering, neemt u contact op met de klantenservice van de Adobe voor hulp.

### Logbestanden openen {#accessing-logs}

U kunt de logbestanden controleren op zowel de bron- als de doelomgeving voor een voltooid proces voor het kopiëren van inhoud.

Om dit te doen, **Inhoudsactiviteit kopiëren** pagina, selecteert u de **Logboeken** actie van het elliptische menu van het exemplaarproces waarvoor u de logboeken wilt herzien en dan kiezen voor welke milieu.

![Logbestanden openen voor kopiëren-inhoudsproces](assets/copy-content-logs.png)

De logbestanden worden naar uw lokale computer gedownload. Als het downloaden niet begint, controleert u de instellingen van de pop-upblokkering.

## Beperkingen {#limitations}

Het gereedschap voor het kopiëren van inhoud heeft de volgende beperkingen.

* Inhoud kan niet van een lagere omgeving naar een hogere omgeving worden gekopieerd.
* Inhoud kan alleen van en naar ontwerpservices worden gekopieerd.
* Kopiëren van inhoud naar andere programma&#39;s is niet mogelijk.
* Het uitvoeren van gelijktijdige bewerkingen voor het kopiëren van inhoud in dezelfde omgeving is niet mogelijk.
* Per inhoudenset kunnen maximaal 50 paden worden opgegeven. Uitgesloten paden zijn niet beperkt.
* Gebruik het gereedschap voor het kopiëren van inhoud niet als een kloon- of spiegelgereedschap omdat het geen verplaatste of verwijderde inhoud op de bron kan bijhouden.
* Het gereedschap voor het kopiëren van inhoud heeft geen versiemogelijkheid en kan niet automatisch gewijzigde inhoud of gemaakte inhoud detecteren in de bronomgeving in een inhoudenset sinds de laatste bewerking voor het kopiëren van inhoud.
   * Als u uw doelomgeving alleen wilt bijwerken met wijzigingen in de inhoud, moet u sinds de laatste bewerking voor het kopiëren van inhoud een inhoudsset maken. Geef vervolgens de paden op in de broninstantie waar wijzigingen zijn aangebracht sinds de laatste bewerking voor het kopiëren van inhoud.
* Versiegegevens worden niet opgenomen in een inhoudskopie.
