<!-- Filename: J5.x:Improving_SEO_with_Strict_Routing_and_SEF_URLs / Display title: SEO Strikte Routering -->

## Inleiding

De optie Strict Routing, geïntroduceerd in Joomla 5.2, verbetert de SEO-prestaties van het platform door strengere routeringsregels toe te staan met behulp van een schakelaar in de *System - SEF* plugin. Het helpt dubbele inhoud te elimineren door consistentere URL's af te dwingen en duplicaten om te leiden naar de juiste URL met een 301-omleiding.

![system sef plugin settings](../../../en/images/seo/seo-system-sef-plugin.png)

### Afdwingen van Achtervoegsels

Momenteel staat Joomla toegang tot URL's met of zonder een achtervoegsel toe wanneer deze optie is ingeschakeld in de opties voor *Globale Configuratie*.

De optie **Afdwingen van een achtervoegsel door omleiding** in de *Systeem - SEF* plugin zorgt voor consistent gedrag van achtervoegsels. Wanneer ingeschakeld, worden GET-verzoeken omgeleid naar een URL met een achtervoegsel als dit ontbreekt. Het zal ook URL's met een queryformaatparameter omleiden naar de schonere URL, waarbij het achtervoegsel wordt vervangen door de formaatparameter waar nodig.

Deze functie wordt naar verwachting de standaardinstelling in Joomla 6.0, waar de optie om deze in of uit te schakelen zal worden verwijderd en deze functionaliteit wordt geïntegreerd in het kernroutingsysteem. Voor nu stelt deze optie gebruikers in staat om het gedrag op live systemen te testen en het uit te schakelen als er onvoorziene problemen ontstaan tijdens de overgangsperiode van Joomla 5.1 naar 6.0.

## Hoe te Toegang Krijgen

Om strikte routing voor SEO in te schakelen:

1. Selecteer het **Plug-ins** item in het *Home Dashboard*.
1. Zoek en open de **System - SEF** plug-in.
2. Stel **Strict Routing** in op *Ja* om strengere URL-afhandeling in te schakelen.
3. Stel **Achtervoegsel afdwingen door omleiden** in op Ja of Nee, afhankelijk van je voorkeur voor het afdwingen van URL-achtervoegsels.

Zodra ingeschakeld, zal Joomla automatisch dubbele URL's omleiden naar de juiste met een 301-omleiding, waardoor SEO wordt verbeterd door inhoud samen te voegen onder één gezaghebbende URL.

## Aanvullende Notities

Deze functie is ontworpen als een voorbereidende stap voor verdere SEO-verbeteringen en is automatisch ingeschakeld voor nieuwe Joomla 5.2-installaties. Het legt de basis voor toekomstige verbeteringen aan het routeringssysteem van Joomla.  
*Vertaald door openai.com*

