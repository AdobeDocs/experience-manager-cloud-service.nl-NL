---
title: SecurBank Sample App voor de Universal Editor
description: Leer over de Universele Redacteur met hands-on ervaring door de App te gebruiken SecurBank, die wordt ontworpen om de macht, de flexibiliteit, en de bruikbaarheid van de Universele Redacteur te tonen om inhoudsverwezenlijking te versnellen.
source-git-commit: 4b7612f423e4e728911920793e9e0a03757c7c9d
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---


# SecurBank Sample App voor de Universal Editor {#securbank}

Leer over de Universele Redacteur met hands-on ervaring door de App te gebruiken SecurBank, die wordt ontworpen om de macht, de flexibiliteit, en de bruikbaarheid van de Universele Redacteur te tonen om inhoudsverwezenlijking te versnellen.

## Vereisten {#prerequisites}

* U moet aan **AEM** [productprofiel](/help/journey-onboarding/assign-profiles-aem.md) om de toepassing SecurBank te installeren.
* U moet [Node.js](https://nodejs.org) versie 20 of hoger geïnstalleerd voor lokale ontwikkeling.

## SecurBank installeren {#installation}

De installatie van de app SecurBank is rechtuit, maar omdat deze veel gebieden van AEM as a Cloud Service raakt, zijn er een aantal stappen mee gemoeid. Hieronder volgt een overzicht van de belangrijkste stappen.

1. [Maak een sandboxprogramma in Cloud Manager.](#create-sandbox-program)
1. [Clone the programma&#39;s git repository and update with the SecurBank AEM project content.](#clone-and-update)
1. [De pijpleiding in werking stellen om het project SecurBank AEM op te stellen.](#run-pipeline)
1. [Win de geloofsbrieven van de Manager van de Wolk voor lokale Web app ontwikkeling terug.](#retrieve-credentials)
1. [Download en configureer de SecureBank-webapp.](#download-web-app)
1. [Voer de SecurBank-webapp uit.](#run-web-app)

In de volgende secties worden de afzonderlijke vereiste taken in detail beschreven.

### Maak een sandboxprogramma in Cloud Manager. {#create-sandbox-program}

U hebt een nieuw Cloud Manager-programma nodig waarin u SecurBank kunt installeren.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie

1. Maak een nieuw sandboxprogramma voor de SecureBank-app.

   * De standaardopties gebruiken bij het selecteren **Oplossingen en invoegtoepassingen**.
   * Zie het document voor meer informatie over het maken van een sandboxprogramma [Sandbox-programma&#39;s maken.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)

### Clone the programma&#39;s git repository and update with the SecurBank AEM project content. {#clone-and-update}

1. Als het programma eenmaal is gemaakt, opent u het en op de knop **Opslagplaatsen** tikken of op de knop **Repo-info openen** om de knop **Info opslagplaats** en bekijk de gegevens die nodig zijn voor toegang tot de it-opslagruimte voor de sandboxomgeving.

   * Zie het document voor meer informatie over hoe u toegang krijgt tot de gegevens in de repository [Toegang tot opslagplaatsen.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

1. De referenties gebruiken in het dialoogvenster **Info opslagplaats** de opslagplaats op uw lokale computer te klonen.

1. Zoek de map van de lokale kloon, open deze en verwijder alle inhoud, behalve de verborgen bestanden en puntbestanden.

1. Haal de recentste SecurBank AEM projectcode van GitHub in [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank) door te klikken **Code** en vervolgens **ZIP downloaden** in de vervolgkeuzelijst.

1. Decomprimeer de inhoud van het ZIP-bestand op uw lokale bestandssysteem en verplaats het naar de nu lege map van de lokale kloon van het sandboxprogramma.

1. Gebruikend de terminal, schakelaar aan de omslag van het gekloonde project, begaan alle inhoud en duw het aan git.

   1. `git add --all`
   1. `git commit -m "Adding SecurBank app code"`
   1. `git push`

### De pijpleiding in werking stellen om het project SecurBank AEM op te stellen. {#run-pipeline}

Met het AEM project voor SecurBank geëngageerd aan de zandbakbewaarplaats, kan het met een pijpleiding worden opgesteld.

1. Terugkeren naar de **Overzicht** van uw sandboxprogramma in Cloud Manager en voer de niet-productiepijplijn voor de volledige stapel uit.

   * Hef alle opties voor de pijpleidingslooppas op.
   * Zie het document voor meer informatie over het uitvoeren van pijpleidingen [Beheren van pijpleidingen.](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines)

### Win de geloofsbrieven van de Manager van de Wolk voor lokale Web app ontwikkeling terug. {#retrieve-credentials}

Voordat u de app SecurBank kunt uitvoeren, hebt u aanmeldingsgegevens van Cloud Manager nodig om de app te verbinden met Cloud Manager.

1. Als de pijpleiding loopt, terugkeer naar **Overzicht** in Cloud Manager en tik of klik op de knop Ovaal naast de naam van de omgeving en selecteer **Ontwerpconsole**.

1. Selecteer in de Developer Console de optie **Integraties** en vervolgens de **Lokale token** tikken of klikken **Token voor lokale ontwikkeling ophalen**.

1. Er wordt een JSON-bestand gemaakt met de toegangstoken. Kopieer alleen het token zelf (de resterende JSON is niet nodig) naar een beveiligde locatie voor gebruik in een volgende stap voordat u de Developer Console sluit en terugkeert naar Cloud Manager.

1. Terug in Cloud Manager, op de **Overzicht** klikt u met de rechtermuisknop op de URL van de omgeving om deze te kopiëren en op een beveiligde locatie op te slaan voor gebruik in een volgende stap.

### Download en configureer de SecureBank-webapp. {#download-web-app}

Nu kunt u de Web-app SecurBank downloaden en vormen.

1. Haal de nieuwste SecureBank-app-code op van GitHub op [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events) door te klikken **Code** en vervolgens **ZIP downloaden** in de vervolgkeuzelijst.

1. Decomprimeer de inhoud van het ZIP-bestand op uw lokale bestandssysteem.

1. Start de gewenste code-editor en open het verborgen omgevingsbestand in het SecureBank-app-project op `summit-2024-l425-ue-z-final-with-events/react-app/.env`.

1. Breng de volgende wijzigingen aan in de `.env` en sla de wijzigingen op.

   * Voor `REACT_APP_HOST_URI` plak de waarde van de eerder gekopieerde URL van uw omgeving.
   * Voor `REACT_APP_DEV_TOKEN` plak de waarde van het eerder gekopieerde lokale ontwikkelingstoken.

### Voer de SecurBank-webapp uit. {#run-web-app}

Met alles wat is ingesteld in zowel Cloud Manager als lokaal, kunt u de SecurBank-webapp uitvoeren.

1. Navigeer op de opdrachtregel van de lokale computer naar de `react-app` map van het SecureBank-app-project dat u hebt gedownload en gedecomprimeerd.

1. In uw `react-app` de SecureBank-app installeren met de `node -i` gebruiken.

1. Start de SecureBank-app met de `npm start` gebruiken.

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

   * En een browservenster open voor de URL `https://localhost:3000`.

      * Merk op dat dit voor ontwikkelingsdoeleinden is en als dusdanig, geen geldig certificaat wordt verstrekt. Daarom moet u mogelijk uw browser op de hoogte stellen zodat deze de pagina kan openen.

Gefeliciteerd! De SecureBank-app wordt nu uitgevoerd in uw browser.

Als de inhoud nog niet wordt weergegeven, controleert u of de **Distribueren naar Dev** pijpleiding die u met succes voltooide.

![De toepassing SecurBank in de browser](assets/securbank.png)
