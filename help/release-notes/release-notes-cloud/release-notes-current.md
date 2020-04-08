---
title: Opmerkingen bij de release 2020.4.0
description: Opmerkingen bij de release 2020.4.0
translation-type: tm+mt
source-git-commit: 77163877bea36f854ac8ea6fbc78cbcf4d58ccc0

---


# Opmerkingen bij de release van AEM als Cloud Service 2020.4.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager weergegeven als Cloud Service 2020.4.0.

## Assets {#assets}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor Experience Manager Assets en Dynamic Media in AEM als Cloud Service Release 2020.4.0.

### Nieuwe functies {#assets-what-is-new}

* [Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) is beschikbaar voor AEM als Cloud Service Assets en ondersteunt toepassingen voor het distribueren van bedrijfsmiddelen. Merk Portal helpt organisaties om aan hun marketingbehoeften te voldoen door goedgekeurde merk- en productmiddelen veilig te distribueren aan externe agentschappen, partners, interne teams en wederverkopers voor downloaden.
   * Poortconfiguratie van merk wordt uitgevoerd via Adobe I/O-console
   * Asset sourcing in Brand Portal wordt nog niet ondersteund met AEM als Cloud Service
* De nieuwe versie van [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) 2.0 wordt ondersteund met AEM als Cloud Service. Adobe Asset Link stroomlijnt de samenwerking tussen creatieve en marketingmedewerkers in het proces voor het maken van inhoud door AEM-middelen aan te sluiten op Creative Cloud-bureaubladapps voor Photoshop, Illustrator en InDesign via het deelvenster Asset Link in de app.
   * AEM als Cloud Service is vooraf geconfigureerd voor Adobe Asset Link, wat resulteert in een [vereenvoudigde configuratie](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html).
   * Asset Link biedt nu ondersteuning voor een [AEM-omgevingsswitch](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink), zodat creatieve gebruikers gemakkelijker verbinding kunnen maken met verschillende AEM-omgevingen (bijvoorbeeld in het geval van ontwerpers van agentschappen die met AEM Assets werken)
* Auto-start voor [naverwerkingswerkstromen](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) kan worden geconfigureerd in de gebruikersinterface voor mapeigenschappen voor specifieke maphiërarchieën.
   * De gebruikersinterface voor mapeigenschappen is vereenvoudigd, met het nieuwe tabblad voor middelenverwerking dat het metagegevensprofiel, het verwerkingsprofiel en de nieuwe workflowconfiguratie voor automatisch opstarten bevat.
* In het dialoogvenster voor het opwerken van bedrijfsmiddelen kunt u een specifiek verwerkingsprofiel selecteren en besluiten om deze opnieuw in submappen te verwerken
* Dynamische media: Toegevoegde Selectieve publicatieconfiguratie, wat betekent dat de activa auto voor veilige voorproef slechts worden gepubliceerd en uitdrukkelijk aan AEM kunnen worden gepubliceerd zonder aan DMS7 voor levering in het openbare domein te publiceren.

### Opgeloste problemen {#assets-bug-fixes}

* Oplossingen in de verwerking van bedrijfsmiddelen
* Oplossingen in Dynamic Media-configuratie en publicatie van elementen naar Dynamic Media-leveringsservice
