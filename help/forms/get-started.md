---
title: Aan de slag met HTML5-formulieren
description: Om aan de slag te gaan, implementeert u het AEM Forms-add-onpakket en importeert u bestaande HTML5-formulieren naar AEM.
content-type: reference
topic-tags: hTML5_forms
discoiquuid: f276d150-8936-4bfb-8475-7ca36815b233
feature: HTML5 Forms,Mobile Forms
exl-id: a3245f05-6ea3-4f90-8981-bfa89d2e7335
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 1496d7517d586c99c5f1001fff13d88275e91d09
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Aan de slag met HTML5-formulieren {#getting-started-with-html-forms}

<span class="preview"> De HTML5 Forms-functionaliteit wordt aangeboden als onderdeel van het programma voor vroege toegang. Als u toegang wilt aanvragen, stuurt u een e-mail van uw officiële (werk)e-mailadres naar aem-forms-ea@adobe.com.
</span>

HTML5-formulieren bieden talrijke mogelijkheden die geschikt zijn voor mobiele apparaten. Het helpt u uw huidige oplossingen en workflows aan tablets of smartphones apparaten met browsers uit te breiden HTML5. Enkele mogelijkheden omvatten:

* **op HTML5-Gebaseerde teruggeven van XFA vormmalplaatjes:** Naast regelmatige PDF forms, kunt u uw bestaande op XFA-Gebaseerde vormen in formaat nu teruggeven HTML5. Hiermee kunt u uw clientplatform uitbreiden naar mobiele apparaten (Apple iPad, Android-tablet, smartphones enzovoort) die HTML5 ondersteunen en Adobe Reader niet met XFA Forms ondersteunen. Voor meer informatie over op HTML5-Gebaseerd teruggevend vermogen, zie [ Inleiding aan HTML5 vormen ](/help/forms/introductionhtml5.md).

* **Beherend Forms:** bovendien omvat AEM nieuwe mogelijkheden om het proces te vereenvoudigen om vormen te organiseren en te beheren. U kunt formulieren activeren, deactiveren, publiceren en hiervan een voorbeeld weergeven.<!--For more information, see [Introduction to managing forms](/help/forms/using/introduction-managing-forms.md).-->

## De omgeving configureren voor HTML5-formulieren {#installing-html-forms}

Voer de volgende stappen uit om het verzenden van formulieren en het correct weergeven van HTML5 Forms mogelijk te maken:

* **voegt de filters van de verzender toe:** werk uw `src/conf.dispatcher.d/filters/filters.any` dossier bij om noodzakelijke verzoeken voor HTML5 Forms toe te staan. Voeg de volgende filterregels toe:

  ```
  /0103 { /type "allow" /method '(HEAD|POST)' /url "/content/xfaforms/profiles/default.submit.html" }  # allow POSTs to form selectors under content
  /0104 { /type "allow" /method '(GET|HEAD|POST)' /url "/*.xdp.html" }
  ```

* **voeg een pakket voor voorlegging toe:** in uw project, voeg een pakket in de `src/main/content/jcr_root/content` omslag toe om de functionaliteit van de vormvoorlegging te steunen.

* **de Invoer HTML5 Forms:** voer uw formulieren van uw lokaal dossiersysteem in AEM Forms in.
