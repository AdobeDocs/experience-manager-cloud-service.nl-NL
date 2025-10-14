---
title: Players registreren in Screens as a Cloud Service
description: Op deze pagina wordt beschreven hoe u spelers kunt registreren in Screens as a Cloud Service.
exl-id: 1a0d6b22-71b1-4f3c-acaa-82d8d9c0f81a
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 1%

---

# Players registreren in Screens as a Cloud Service {#registering-players-screens-cloud}

Nadat u spelers voor Screens as a Cloud Service hebt geïnstalleerd en geconfigureerd, moet u de spelers registreren.

## Doelstelling {#objective}

Met dit document krijgt u meer inzicht in het registreren van spelers bij de Screens Services Provider. Na het lezen moet u in staat zijn om:

* begrijpen hoe spelers worden geregistreerd
* hoe u het registratieproces van Screens Services Provider kunt voltooien

## Stappen om een Screens Player te registreren {#register-players}

Nadat u de speler op Screens as a Cloud Service hebt geïnstalleerd, kunt u de speler registreren bij de Screens Services Provider.

Volg de onderstaande stappen om uw speler te registreren:

1. Meld u aan bij de Screens Services Provider.

1. Navigeer aan **Codes van de Registratie** onder **beheer van Players** van het linkernavigatievenster en klik **creeer code**.

   >[!NOTE]
   >Als er geen geldige/niet-verlopen codes bestaan, klikt u op Code maken en voert u een naam voor de code in. Kies vervolgens de gewenste vervalinstellingen.

   ![afbeelding](/help/screens-cloud/assets/player/register-player1.png)

1. Vul de volgende gebieden in **creeer een de dialoogdoos van de registratiecode**:

   ![afbeelding](/help/screens-cloud/assets/player/register-player2.png)

   1. **Naam van de Code van de Registratie**: Naam voor uw registratiecode
   1. **Vervaldatum van de Code van de Registratie**: Datum van vervaldatum voor uw registratiecode
   1. **Gebruik van de Beperking**: Knevel de knoop om de gebruiksgrens van uw registratiecode uit te schakelen. Standaard is de optie Gebruik beperken uitgeschakeld.
   1. **Limiet van het Gebruik**: Kies het aantal voor uw gebruiksgrens

1. Klik **creëren** om de registratiecode tot stand te brengen. U kunt de speler met de registratiecode in de lijst zien.

   ![afbeelding](/help/screens-cloud/assets/player/register-player3.png)

1. Klik de waarde onder de kolom **CODE VAN DE REGISTRATIE** om de waarde aan het klembord te kopiëren.

1. Plak deze waarde in het **ingaan code** gebied op het **lusje van de Registratie van de Speler** van Admin UI van de speler van AEM Screens en klik **Register**.

   ![afbeelding](/help/screens-cloud/assets/player/register-player4.png)


1. Wanneer u de code hebt toegevoegd, ziet u dat de speler nu is geregistreerd via de beheerdersinterface van de speler.

   ![afbeelding](/help/screens-cloud/assets/player/register-player5.png)

1. U zou deze speler nu moeten zien verschijnen in **Players** van het linkernavigatievenster. De code die in de Dienstverlener van Screens toont past het **paneel van de Informatie van het Systeem** van Admin UI onder de Code van de Speler aan.

   ![afbeelding](/help/screens-cloud/assets/player/register-player6.png)

   >[!IMPORTANT]
   >**Aanbeveling van de Beste praktijken van de Veiligheid terwijl het gebruiken van de Code van de Registratie**
   >U kunt het gebruik van de registratiecode het beste beperken. Als een registratiecode gecompromitteerd is, maar een grens van 100 registraties heeft, dan kan de aanvaller slechts tot dat aantal, maar niet meer registreren. U kunt de gebruikslimiet altijd bijwerken nadat de registratiecode is gemaakt en enkele spelers van de klant al zijn geregistreerd. Als de klant ongebruikelijke registratieactiviteit voor een specifieke registratiecode opmerkt, kunnen zij de grens in real time verminderen terwijl zij onderzoeken en kunnen het aantal terugverhogen als het een vals alarm was, zonder de reeds geregistreerde spelers te beïnvloeden.


## Volgende functies {#whats-next}

Nu, dat u de speler aan de wijze van de Wolk hebt geïnstalleerd en gevormd, zou u uw as a Cloud Service reis van Screens door het document te herzien moeten voortzetten, [&#x200B; toewijzend Speler aan een Vertoning in Screens as a Cloud Service &#x200B;](/help/screens-cloud/managing-players-registration/assigning-player-display.md) van Screens Services Provider.
