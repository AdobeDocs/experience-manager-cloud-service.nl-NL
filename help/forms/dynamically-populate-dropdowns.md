---
title: Hoe te om drop-down lijsten dynamisch te bevolken?
description: Leer hoe u een keuzelijst met trapsgewijze opmaak maakt of vervolgkeuzelijsten dynamisch vult.
uuid: b3408aee-ac24-43af-a380-a5892abf0248
content-type: reference
topic-tags: customization
discoiquuid: ad6db3fd-0d26-4241-bf73-be74b7f6e509
source-git-commit: e2f2aa18e2412bc92d1385a125281ecfb81f2ce8
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# Vervolgkeuzelijsten dynamisch vullen {#dynamically-populating-drop-down-lists}

## Vereisten {#prerequisites}

* [OSGI-pakketten maken](https://helpx.adobe.com/experience-manager/using/creating-osgi-bundles-digital-marketing.html)
* [AEM ontwikkelen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/components-templates/overview.html#developing)
* [Adaptief formulier maken](creating-adaptive-form.md)
* [Aangepast formulier ontwerpen](introduction-forms-authoring.md)

## Procedure voor het dynamisch vullen van vervolgkeuzelijsten {#procedure-to-dynamically-populate-drop-down-lists}

Overweeg een scenario waar u het **Staat** vervolgkeuzelijst op basis van een waarde die u in het dialoogvenster **Land** vervolgkeuzelijst. Als u Australië selecteert in het dialoogvenster **Land** vervolgkeuzelijst, de **Staat** in de vervolgkeuzelijst worden de staten in Australië weergegeven. De volgende procedure beschrijft hoe te om deze taak te verwezenlijken.

1. Creeer een project met de volgende modules:

   * De bundel die de logica bevat om de drop-down te bevolken, die in dit geval een servlet is.
   * De inhoud, die het .jar dossier insluit en een drop-down middel heeft. De servlet wijst naar deze resource.

1. Schrijf een servlet die op het Land van de verzoekparameter wordt gebaseerd, die een serie terugkeert die de namen van staten binnen het land bevat.

   ```java
   @Component(metatype = false)
   @Service(value = Servlet.class)
   @Properties({
           @Property(name = "sling.servlet.resourceTypes", value = "/apps/populatedropdown"),
           @Property(name = "sling.servlet.methods", value = {"GET", "POST"}),
           @Property(name = "service.description", value = "Populate states dropdown based on country value")
   })
   public class DropDownPopulator extends SlingAllMethodsServlet {
       private Logger logger = LoggerFactory.getLogger(DropDownPopulator.class);
   
       protected void doPost(SlingHttpServletRequest request,
                             final SlingHttpServletResponse response)
               throws ServletException, IOException {
           response.setHeader("Access-Control-Allow-Origin", "*");
           response.setContentType("application/json");
           response.setCharacterEncoding("UTF-8");
           try {
               String US_STATES[] = {"0=Alabama",
                       "1=Alaska",
                       "2=Arizona",
                       "3=Arkansas",
                       "4=California",
                       "5=Colorado",
                       "6=Connecticut",
                       "7=Delaware",
                       "8=Florida",
                       "9=Georgia",
                       "10=Hawaii",
                       "11=Idaho",
                       "12=Illinois",
                       "13=Indiana",
                       "14=Iowa",
                       "15=Kansas",
                       "16=Kentucky",
                       "17=Louisiana",
                       "18=Maine",
                       "19=Maryland",
                       "20=Massachusetts",
                       "21=Michigan",
                       "22=Minnesota",
                       "23=Mississippi",
                       "24=Missouri",
                       "25=Montana",
                       "26=Nebraska",
                       "27=Nevada",
                       "28=New Hampshire",
                       "29=New Jersey",
                       "30=New Mexico",
                       "31=New York",
                       "32=North Carolina",
                       "33=North Dakota",
                       "34=Ohio",
                       "35=Oklahoma",
                       "36=Oregon",
                       "37=Pennsylvania",
                       "38=Rhode Island",
                       "39=South Carolina",
                       "40=South Dakota",
                       "41=Tennessee",
                       "42=Texas",
                       "43=Utah",
                       "44=Vermont",
                       "45=Virginia",
                       "46=Washington",
                       "47=West Virginia",
                       "48=Wisconsin",
                       "49=Wyoming"};
               String AUSTRALIAN_STATES[] = {"0=Ashmore and Cartier Islands",
                       "1=Australian Antarctic Territory",
                       "2=Australian Capital Territory",
                       "3=Christmas Island",
                       "4=Cocos (Keeling) Islands",
                       "5=Coral Sea Islands",
                       "6=Heard Island and McDonald Islands",
                       "7=Jervis Bay Territory",
                       "8=New South Wales",
                       "9=Norfolk Island",
                       "10=Northern Territory",
                       "11=Queensland",
                       "12=South Australia",
                       "13=Tasmania",
                       "14=Victoria",
                       "15=Western Australia"};
               String country = request.getParameter("country");
               JSONArray stateJsonArray = new JSONArray();
               if (country.length() > 0) {
                   if ("australia".equalsIgnoreCase(country)) {
                       stateJsonArray = new JSONArray();
                       for (String state : AUSTRALIAN_STATES) {
                           stateJsonArray.put(state);
                       }
                   } else if ("unitedstates".equalsIgnoreCase(country)) {
                       stateJsonArray = new JSONArray();
                       for (String state : US_STATES) {
                           stateJsonArray.put(state);
                       }
                   }
                   response.setContentType("application/json");
                   response.getWriter().write(stateJsonArray.toString());
               }
   
           } catch ( Exception e) {
               logger.error(e.getMessage(), e);
           }
       }
   }
   ```

1. Maak een vervolgkeuzelijst onder een bepaalde maphiërarchie in apps (maak bijvoorbeeld een knooppunt onder /apps/myfolder/demo). Zorg ervoor dat de `sling:resourceType` parameter voor het knooppunt is dezelfde als die waaraan de servlet-punten (/apps/populatedropdown) wijzen.

   ![Een vervolgkeuzelijst maken](assets/dropdown-node.png)

1. Verpak het inhoudsknooppunt en sluit het .jar-bestand in op een bepaalde locatie (bijvoorbeeld /apps/mijnmap/demo/install/). Implementeer hetzelfde bestand op de server.
1. Maak een adaptief formulier en voeg er twee vervolgkeuzelijsten aan toe: Land en Staat. De lijst Land kan de namen van landen bevatten. In de lijst Frame kunnen dynamisch de namen worden ingevuld van staten voor het land dat u in de eerste lijst selecteert.

   Voeg de namen van de landen toe die u wilt weergeven in de lijst Land. Voeg in de lijst Staat een script toe om het te vullen op basis van de naam van het land in de lijst Land.

   ![Landnamen toevoegen](assets/country-dropdown.png) ![Script toevoegen om statusnamen te vullen](assets/state-dropdown.png) ![Vervolgkeuzelijsten voor landen en staten](assets/2dropdowns.png)

   ```javascript
   JSON.parse(
       $.ajax({
           url: "/apps/myfolder/demo/dropdown",
           type: "POST",
           async: false,
           data: {"country": country.value},
            success: function(res){},
            error : function (message) {
                 guideBridge._guide.logger().log(message);
                 successFlag = false;
                 }
              })
   .responseText);
   ```

Het pakket Inhoud dat een voorbeeld van een adaptieve vorm (demo/AFdemo) bevat en de bovenstaande code is geïmplementeerd.

[Bestand ophalen](assets/dropdown-demo-content-1.0.1-snapshot.zip)
