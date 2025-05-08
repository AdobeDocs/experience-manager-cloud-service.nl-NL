---
title: SecurBank Sample App voor de Universal Editor
description: Leer over de Universele Redacteur met hands-on ervaring door de App te gebruiken SecurBank, die wordt ontworpen om de macht, de flexibiliteit, en de bruikbaarheid van de Universele Redacteur te tonen om inhoudsverwezenlijking te versnellen.
exl-id: 97e1395f-b51e-4cee-b1d0-2466a08f96af
feature: Developing
role: Admin, Architect, Developer
source-git-commit: c4dcb1cecb756f746ecb856fcfd65d73833a5ee0
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# SecurBank Sample App voor de Universal Editor {#securbank}

Leer over de Universele Redacteur met hands-on ervaring door de App te gebruiken SecurBank, die wordt ontworpen om de macht, de flexibiliteit, en de bruikbaarheid van de Universele Redacteur te tonen om inhoudsverwezenlijking te versnellen.

## Vereisten {#prerequisites}

* U moet aan de **Beheerder van AEM** [ productprofiel ](/help/journey-onboarding/assign-profiles-aem.md) worden toegewezen om app te installeren SecurBank.
* U moet [ Node.js ](https://nodejs.org) versie 20 hebben of hoger geïnstalleerd voor lokale ontwikkeling.

## SecurBank installeren {#installation}

De installatie van de app SecurBank is rechtuit, maar omdat deze veel gebieden van AEM as a Cloud Service raakt, zijn er een aantal stappen mee gemoeid. Hieronder volgt een overzicht van de belangrijkste stappen.

1. [ creeer een zandbakprogramma in Cloud Manager ](#create-sandbox-program).
1. [ kloon de git bewaarplaats van het programma en werk met het SecurBank AEM- projectinhoud ](#clone-and-update) bij.
1. [ stel de pijpleiding in werking om het project SecurBank AEM ](#run-pipeline) op te stellen.
1. [ wint de geloofsbrieven van Cloud Manager voor lokale Web app ontwikkeling ](#retrieve-credentials) terug.
1. [ Download en vorm het Web SecureBank app ](#download-web-app).
1. [ stel het Web-app SecureBank ](#run-web-app) in werking.

In de volgende secties worden de afzonderlijke vereiste taken in detail beschreven.

### Een sandboxprogramma maken in Cloud Manager. {#create-sandbox-program}

U hebt een nieuw Cloud Manager-programma nodig waarin u SecurBank kunt installeren.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie

1. Maak een nieuw sandboxprogramma voor de SecureBank-app.

   * Gebruik de standaardopties wanneer het selecteren van **Oplossingen &amp; toe:voegen-ONS**.
   * Voor details op hoe te om een zandbakprogramma tot stand te brengen, te zien gelieve het document [ Creërend Programma Sandbox ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md).

### Clone the programma&#39;s git repository and update with the SecurBank AEM project content. {#clone-and-update}

1. Zodra het programma wordt gecreeerd, open het en op het **lusje van de Bewaarplaatsen**, tik of klik de **knoop van Info van de Reparatie van de Toegang** om de **dialoog van Info van de Bewaarplaats** te openen en de geloofsbrieven noodzakelijk te bekijken om tot de git bewaarplaats voor het zandbakmilieu toegang te hebben.

   * Voor details op hoe te om tot uw gegevensopslagplaats toegang te hebben, te zien gelieve het document [ Toegang hebbend tot Bewaarplaatsen ](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

1. Gebruikend de geloofsbrieven in de **dialoog van Info van de Bewaarplaats**, kloon de bewaarplaats op uw lokale machine.

1. Zoek de map van de lokale kloon, open deze en verwijder alle inhoud, behalve de verborgen bestanden en puntbestanden.

1. Haal de recentste het projectcode van SecureBank AEM van GitHub bij [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank` terug ](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank) door **Code** en dan **Download ZIP** in dropdown te klikken.

1. Decomprimeer de inhoud van het ZIP-bestand op uw lokale bestandssysteem en verplaats het naar de nu lege map van de lokale kloon van het sandboxprogramma.

1. Gebruikend de terminal, schakelaar aan de omslag van het gekloonde project, begaan alle inhoud en duw het aan git.

   1. `git add --all`
   1. `git commit -m "Adding SecurBank app code"`
   1. `git push`

### Voer de pijpleiding uit om het project SecurBank AEM te implementeren. {#run-pipeline}

Als het AEM-project voor SecurBank is vastgelegd in de sandboxopslagplaats, kan het worden geïmplementeerd met een pijplijn.

1. Terugkeer naar het **Overzicht** lusje van uw zandbakprogramma in Cloud Manager en stel de volledig-stapel non-production pijpleiding in werking.

   * Hef alle opties voor de pijpleidingslooppas op.
   * Voor meer informatie over het runnen van pijpleidingen, zie gelieve het document [ Leiden Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines).

### Haal Cloud Manager-referenties op voor de ontwikkeling van lokale webapps. {#retrieve-credentials}

Voordat u de SecureBank-app kunt uitvoeren, hebt u Cloud Manager-referenties nodig om de app te verbinden met Cloud Manager.

1. Aangezien de pijpleiding loopt, terugkeer aan het **Overzicht** lusje in Cloud Manager, en ontleed of klik de ellipsknoop naast de milieunaam en selecteer **Developer Console**.

1. In Developer Console selecteert het **lusje van de Integraties** toen het **Lokale Symbolische** lusje en de kraan of klikt **krijgt Token van de Lokale Ontwikkeling**.

1. Er wordt een JSON-bestand gemaakt met de toegangstoken. Kopieer alleen het token zelf (de resterende JSON is niet nodig) naar een beveiligde locatie voor gebruik in een volgende stap voordat u de Developer Console sluit en terugkeert naar Cloud Manager.

1. Terug in Cloud Manager, op het **Overzicht** lusje, klik URL van het milieu met de rechtermuisknop aan om het te kopiëren en het te bewaren in een veilige plaats voor gebruik in een toekomstige stap.

### Download en configureer de SecureBank-webapp. {#download-web-app}

Nu kunt u de Web-app SecurBank downloaden en vormen.

1. Haal de recentste SecureBank app code van GitHub bij [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events` terug ](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events) door **Code** te klikken en dan **ZIP van de Download** in dropdown.

1. Decomprimeer de inhoud van het ZIP-bestand op uw lokale bestandssysteem.

1. Start de gewenste code-editor en open het verborgen omgevingsbestand in het SecureBank-app-project op `summit-2024-l425-ue-z-final-with-events/react-app/.env` .

1. Breng de volgende wijzigingen aan in het `.env` -bestand en sla de wijzigingen op.

   * Voor `REACT_APP_HOST_URI` plakt u de waarde van de eerder gekopieerde URL van de omgeving.
   * Voor `REACT_APP_DEV_TOKEN` plakt u de waarde van het eerder gekopieerde lokale ontwikkelingstoken.

### Voer de SecurBank-webapp uit. {#run-web-app}

Met alles wat zowel in Cloud Manager als lokaal is ingesteld, kunt u de SecurBank-webapp uitvoeren.

1. Navigeer op de opdrachtregel van uw lokale computer naar de map `react-app` van het SecureBank-app-project dat u hebt gedownload en gedecomprimeerd.

1. Installeer de SecureBank-toepassing in uw `react-app` -map met de opdracht `node -i` .

1. Start de SecureBank-app met de opdracht `npm start` nadat deze is geïnstalleerd.

1. Als de installatie en het begin succesvol waren, zult u zien:

* De volgende output in de terminal.

  ```text
  Compiled successfully!
  
  You can now view securbank in the browser.
  
    Local:            https://localhost:3000
    On Your Network:  https://192.168.1.15:3000
  
  Note that the development build is not optimized.
  To create a production build, use npm run build.
  
  webpack compiled successfully
  ```

   * En er wordt een browservenster geopend naar de URL `https://localhost:3000` .

      * Merk op dat dit voor ontwikkelingsdoeleinden is en als dusdanig, geen geldig certificaat wordt verstrekt. Daarom moet u mogelijk uw browser op de hoogte stellen zodat deze de pagina kan openen.

Gefeliciteerd! De SecureBank-app wordt nu uitgevoerd in uw browser.

Als de inhoud nog niet verschijnt, zorg ervoor dat **aan Dev** pijpleiding opstelt die u met succes voltooide.

![ SecureBank app in browser ](assets/securbank.png)

{{ue-headless-auth}}

