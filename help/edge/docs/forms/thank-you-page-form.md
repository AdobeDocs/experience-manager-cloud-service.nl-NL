---
title: Hartelijk dank voor EDS Forms configureren
description: Hartelijk dank voor EDS Forms configureren
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0604838311bb9ab195789fad755b0910e09519fd
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 1%

---


# Omleiding van formulierblokken configureren

U kunt het formulierblok zo configureren dat het naar een andere pagina op uw website wordt omgeleid in plaats van naar de standaardpagina &quot;dankuwel&quot;. Een andere pagina instellen als omleidingsdoel

1. Open de `[EDS Project]/blocks/form/form.js` bestand voor bewerking.

   ![code voor het knooppunt voor bedankt](/help/edge/assets/change-thankyou-node.png)

1. Wijzig de `thankyou` knoop in de volgende lijn aan knoop van uw keus:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   Bijvoorbeeld:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'home';
   ```

   >[!NOTE]
   >
   > Zorg ervoor dat er een documentpagina met dezelfde naam wordt gemaakt in de projectmap voor Edge Delivery Service op Microsoft SharePoint of Google Sheets, als deze nog niet is gemaakt.


1. Ga aan controle-binnen de bijgewerkte omslag &quot;form.js&quot;en zijn onderliggende dossiers aan uw project van de Dienst van de Levering van de Rand op GitHub te werk. Deze update zorgt ervoor dat het formulier nu wordt omgeleid naar het bijgewerkte knooppunt zoals opgegeven.
