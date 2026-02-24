---
title: Problemen met AEM bij ontwerpen oplossen
description: Sommige problemen die u kunt tegenkomen bij het gebruik van AEM
badgeSaas: label="AEM Sites" type="Positive" tooltip="van toepassing op AEM Sites)."
exl-id: b9c0584d-255e-486d-b829-09e07499ecd2
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---

# Problemen met AEM bij ontwerpen oplossen {#troubleshooting-aem-when-authoring}

In de volgende sectie worden enkele problemen beschreven die u kunt tegenkomen bij het gebruik van AEM, samen met suggesties voor het oplossen van problemen met deze problemen.

## Oude paginaversie blijft op gepubliceerde site staan {#old-page-version-still-on-published-site}

* **Uitgave**:
   * U hebt veranderingen in een pagina aangebracht en de pagina aan publiceren plaats gepubliceerd, maar de *oude* versie van de pagina wordt nog getoond op publiceren plaats.
* **Reden**:
   * Dit kan verschillende oorzaken hebben, meestal het geheime voorgeheugen (of uw lokale browser of Dispatcher), hoewel het soms een kwestie met de replicatierij kan zijn.
* **Oplossingen**:
   * Hier zijn verschillende mogelijkheden:
   * Controleer of de pagina correct is gerepliceerd. Controleer de paginastatus en, indien nodig, de status van de replicatiewachtrij.
   * Wis de cache in uw lokale browser en open de pagina opnieuw.
   * Voeg `?` toe aan het einde van de pagina-URL. Bijvoorbeeld:
      * `http://<host>:<port>/sites.html/content?`
      * Hiermee wordt de pagina direct bij AEM aangevraagd en wordt de Dispatcher overgeslagen. Als u de bijgewerkte pagina ontvangt, geeft dit aan dat u de Dispatcher-cache moet wissen.
   * Neem contact op met uw systeembeheerder als er problemen zijn met de replicatiestijden.

## Componenthandelingen niet zichtbaar op werkbalk {#component-actions-not-visible-on-toolbar}

* **Uitgave**:
   * Het volledige bereik van toepasselijke componentacties is niet zichtbaar wanneer u een inhoudspagina bewerkt in de auteursomgeving.
* **Reden**:
   * In zeldzame gevallen kan een eerdere actie gevolgen hebben voor de werkbalk.
* **Oplossing**:
   * Vernieuw de pagina.
