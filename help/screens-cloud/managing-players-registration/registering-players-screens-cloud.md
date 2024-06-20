---
title: Afspeellagen registreren in as a Cloud Service schermen
description: Op deze pagina wordt beschreven hoe u spelers kunt registreren in as a Cloud Service schermen.
exl-id: 1a0d6b22-71b1-4f3c-acaa-82d8d9c0f81a
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 1%

---

# Afspeellagen registreren in as a Cloud Service schermen {#registering-players-screens-cloud}

Nadat u spelers voor de as a Cloud Service schermen hebt geïnstalleerd en geconfigureerd, moet u de spelers registreren.

## Doelstelling {#objective}

Met dit document krijgt u meer inzicht in het registreren van spelers bij de Screens Services Provider. Na het lezen moet u in staat zijn om:

* begrijpen hoe spelers worden geregistreerd
* hoe te om het registratieproces van de Leverancier van de Diensten van het Scherm te voltooien

## Stappen om een schermspeler te registreren {#register-players}

Nadat u de speler op de as a Cloud Service schermen hebt geïnstalleerd, kunt u de speler registreren bij Screens Services Provider.

Volg de onderstaande stappen om uw speler te registreren:

1. Meld u aan bij de leverancier van schermservices.

1. Navigeren naar **Registratiecodes** krachtens **Beheer van spelers** in het linkernavigatievenster en klik op **Code maken**.

   >[!NOTE]
   >Als er geen geldige/niet-verlopen codes bestaan, klikt u op Code maken en voert u een naam voor de code in. Kies vervolgens de gewenste vervalinstellingen.

   ![afbeelding](/help/screens-cloud/assets/player/register-player1.png)

1. De volgende velden invullen **Een registratiecode maken** dialoogvenster:

   ![afbeelding](/help/screens-cloud/assets/player/register-player2.png)

   1. **Registratiecode**: Naam voor uw registratiecode
   1. **Vervaldatum registratiecode**: Vervaldatum voor je inschrijvingscode
   1. **Gebruik beperken**: Schakel de knop in en uit om de gebruikslimiet van de registratiecode uit te schakelen. Standaard is de optie Gebruik beperken uitgeschakeld.
   1. **Gebruikslimiet**: Kies het nummer voor uw gebruikslimiet

1. Klikken **Maken** om de registratiecode te maken. U kunt de speler met de registratiecode in de lijst zien.

   ![afbeelding](/help/screens-cloud/assets/player/register-player3.png)

1. Klik op de waarde onder de kolom **REGISTRATIECODE**  om de waarde naar het klembord te kopiëren.

1. Plak deze waarde in het dialoogvenster **Code invoeren** in het veld **Spelerregistratie** van de Admin UI van de speler van AEM Screens en klik **Registreren**.

   ![afbeelding](/help/screens-cloud/assets/player/register-player4.png)


1. Wanneer u de code hebt toegevoegd, ziet u dat de speler nu is geregistreerd via de beheerdersinterface van de speler.

   ![afbeelding](/help/screens-cloud/assets/player/register-player5.png)

1. Deze speler wordt nu weergegeven in **Players** in het navigatievenster aan de linkerkant. De code die in de Dienstverlener van de Vraag van het Scherm wordt getoond past aan **Systeeminformatie** uit de beheerinterface onder Player Code.

   ![afbeelding](/help/screens-cloud/assets/player/register-player6.png)

   >[!IMPORTANT]
   >**Aanbevolen werkwijzen voor beveiliging tijdens het gebruik van registratiecode**
   >U kunt het gebruik van de registratiecode het beste beperken. Als een registratiecode gecompromitteerd is, maar een grens van 100 registraties heeft, dan kan de aanvaller slechts tot dat aantal, maar niet meer registreren. U kunt de gebruikslimiet altijd bijwerken nadat de registratiecode is gemaakt en enkele spelers van de klant al zijn geregistreerd. Als de klant ongebruikelijke registratieactiviteit voor een specifieke registratiecode opmerkt, kunnen zij de grens in real time verminderen terwijl zij onderzoeken en kunnen het aantal terugverhogen als het een vals alarm was, zonder de reeds geregistreerde spelers te beïnvloeden.


## Volgende functies {#whats-next}

Nu u de speler hebt geïnstalleerd en geconfigureerd voor de cloud-modus, moet u de as a Cloud Service reis van de schermen voortzetten door het document opnieuw te bekijken. [Speler toewijzen aan een as a Cloud Service weergave in schermen](/help/screens-cloud/managing-players-registration/assigning-player-display.md) van Screens Services Provider.
