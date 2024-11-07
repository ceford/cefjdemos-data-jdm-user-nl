<!-- Filename: J6.x:Article_Access_Restriction / Display title: Artikel: Toegangsbeperking  -->

## Inleiding

Er zijn verschillende redenen om de toegang tot artikelen op een website te beperken. Sommige inhoud kan privé zijn voor specifieke gebruikers, zoals leden van een commissie. Of de site kan commerciële inhoud bevatten waarvoor betaald moet worden om te bekijken. Joomla biedt een krachtig Toegangscontrolesysteem (Access Control List, ACL) om de toegang te beperken. Dit wordt beschreven in een apart artikel over [Toegangscontrole](jdocmanual?article=user/users/access-control) in de Gebruikerssectie van deze handleiding.

Dit artikel beschrijft de implementatie van toegangsbeperking in het *Artikel: Bewerken* formulier. 

## Beperking op Toegangsniveau

Joomla biedt de Toegangsniveaus zoals te zien in de volgende schermafbeelding:

![Gebruikerstoegangsniveaus](../../../en/images/articles/article-access-user-groups.png)

De toegangsniveaus verschijnen in het tabblad *Inhoud* van het formulier *Artikel: Bewerken*.

- **Openbaar** Kan door iedereen bekeken worden - zowel gebruikers die zijn ingelogd 
  als gebruikers die niet zijn ingelogd.
- **Gast** Dit toegangsniveau beperkt de toegang tot gebruikers die **NIET** 
  zijn ingelogd.
- **Geregistreerd** Dit niveau beperkt de toegang tot gebruikers die zijn ingelogd.
  Een artikel met *Toegang* ingesteld op *Geregistreerd* vereist een frontend-inlog 
  voordat het artikel kan worden bekeken.
- **Speciaal** Dit niveau beperkt de toegang tot gebruikers die zijn ingelogd 
  en tot een specifieke gebruikersgroep behoren anders dan Geregistreerd. Bovendien is het 
  mogelijk om inhoud te differentiëren die sommige ingelogde gebruikers kunnen 
  bekijken, maar anderen niet. Dit kan bijvoorbeeld een website zijn waar 
  abonnementen vereist zijn om toegang te krijgen tot extra inhoud.
- **Supergebruikers** Als u dit niveau instelt, betekent dit dat alleen een 
  Supergebruiker toegang tot het artikel kan krijgen. Dit kan worden gebruikt voor 
  artikelen over sitebeheer.

Merk op dat deze lijst gaat over **Bekijken** of toestemming hebben om inhoud te 
bekijken. U kunt aanvullende Toegangsniveaus en Gebruikersgroepen maken om 
aan te passen wie wat kan zien.

## Gedeeltelijke Beperking om Meer te Lezen

Soms wil je misschien de toegang tot een artikel beperken, maar wel onbeperkte toegang bieden tot een voorproefje van het artikel. Dit is een veelgebruikte manier om betaalde toegang tot commercieel inhoud te implementeren. Procedure:

- Zoek het artikel dat gedeeltelijk beperkt moet worden in de *Artikelen* lijst en open het voor bewerking.
- Voeg een *Pagina-einde* in na de eerste alinea. Het Pagina-einde instrument bevindt zich onderaan de *CMS Inhoud* lijst in het TinyMCE artikel bewerkingsformulier.
- Stel het *Toegang*-niveau van het artikel in op *Geregistreerd*.
- Selecteer **Opslaan & Sluiten** in de Werkbalk.

### Toegang tot Artikelen afzonderlijk beperken

Open het *Categorie Blog* of *Aanbevolen Artikelen* menu-item waar het artikel zal verschijnen.

- Stel op het tabblad **Opties** **Ongeautoriseerde Links** in op **Ja**. Dit bevindt zich onderaan de lijst met Opties.
- Selecteer **Opslaan & Sluiten** in de Werkbalk.

### Toegang tot Artikelen Globaal beperken

* Stel de relevante Categorieën in op weergaveniveau *Publiek*, anders zijn menu-items niet zichtbaar voor gebruikers die niet zijn ingelogd.
* Stel de artikelen in de relevante Categorieën in op weergaveniveau Geregistreerd. Dit kan worden gedaan door de artikelen te selecteren en de *Batch* knop te gebruiken.
* Ga naar **Inhoud → Artikelen → Opties**
* Stel **Ongeautoriseerde Links** in op **Ja** in het tabblad Artikelen. Als dit op Ja is ingesteld, worden links naar geregistreerde inhoud weergegeven, zelfs als u niet bent ingelogd. U moet inloggen om toegang te krijgen tot het volledige item.

**Opmerking:** Tekst in een Artikel zonder een *Lees Meer* breuk wordt behandeld als alle Intro tekst. Als je een Artikel hebt dat alleen voor Geregistreerde gebruikers bedoeld is, maar geen Lees Meer heeft, dan zal het hele artikel zichtbaar zijn voor alle gebruikers. Voeg dus een Lees Meer toe aan het artikel!

*Vertaald door openai.com*

