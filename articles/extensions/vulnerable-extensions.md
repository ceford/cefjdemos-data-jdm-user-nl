<!-- Filename: jdocmanual?manual=user&heading=extensions&filename=vulnerable-extensions.md / Display title: Kwetsbare Extensies  -->

## Uitbreidingsbronnen

Iedereen kan een Joomla!-uitbreiding schrijven en distribueren als een dienst aan de mondiale gemeenschap. Dergelijke **derde partij** uitbreidingen kunnen worden gevonden op websites van professionele uitbreidingsontwikkelaars, persoonlijke blogwebsites, GitHub en soortgelijke repositories en de Joomla Extensions Directory-website.

## Kwetsbare Extensies

Zeer weinig bronnen bieden opzettelijk kwaadaardige extensies aan. Meestal is een **kwetsbare extensie** er een die na de eerste release een beveiligingskwetsbaarheid blijkt te bevatten (of bij te dragen aan).

Kwetsbare extensies zijn niet noodzakelijk slecht gecodeerd. Naarmate het web evolueert, veranderen technische vereisten en algemeen geaccepteerde programmeerpraktijken. Actieve projecten brengen nieuwe versies uit van hun extensies naarmate de vereisten veranderen en lossen snel gemelde kwetsbaarheden op.

Als je je zorgen maakt over een van je extensies, zou je de Joomla Kwetsbare Extensieslijst (VEL) moeten raadplegen die informatie bevat over 240+ meestal oude extensies.

## De JED Checker

Als je je zorgen maakt over een extensie die niet in de VEL verschijnt, kun je de JED Checker-extensie gebruiken. Dit is een extensie die wordt gebruikt om extensies te controleren die ingediend zijn om in de Joomla Extensions Directory lijst te verschijnen. Het wordt geïnstalleerd zoals elke andere extensie. Bij gebruik accepteert het een extensie-zipbestand en onderzoekt het de inhoud ervan op naleving van de JED-standaarden. Het is uiterst nuttig, zelfs voor extensies die niet in de JED-lijst verschijnen. Hier is een voorbeeldscreenshot:

![jed checker resultaat](../../../en/images/extensions/extensions-jed-checker.png)

De 400 PHP-bestanden zonder GPL-licentiekennisgeving bevinden zich in externe bibliotheken met een andere licentie. De 30 bestanden die door het Joomla Anti-Malware Scan Script zijn geïdentificeerd, bevinden zich ook in die externe bibliotheken. Er is werk aan de winkel voor de bestanden die de JEXEC-beveiliging missen!

## Verwijderen van een Kwetsbare Extensie

### Maak een Lijst van Bestanden om te Verwijderen

Als je het kunt vinden, lees dan het xml-bestand van de extensie om precies te bepalen welke mappen, bestanden en databasetabellen aan je systeem zijn toegevoegd. Het XML-bestand bevindt zich in het oorspronkelijke zip-archief dat is gebruikt tijdens het installatieproces van de extensie. Bijvoorbeeld, het zip-archief voor een extensie genaamd mod_vulnerable zou een XML-bestand bevatten genaamd mod_vulnerable.xml, en zou een lijst met bestanden zoals de volgende kunnen bevatten:

```
    mod_vulnerable.php
    mod_vulnerable/vulnerable_file.txt
    mod_vulnerable/another_vulnerable_file.txt
    mod_vulnerable/yet_another_vulnerable_file.txt
    mod_vulnerable/index.html
```

### De-installeer Via de Joomla Installer

Gebruik de Installer in de Joomla! Administrator backend om de kwetsbare extensie te de-installeren. Mogelijk moet je ook gerelateerde modules, componenten of plugins de-installeren.

### Controleer of het Verwijderingsproces Voltooid was

Vertrouw er niet op dat de extensie al zijn bestanden veilig verwijdert. Vergelijk mappen en bestanden op je systeem met de XML-lijst van de extensie om te verzekeren dat alle gerelateerde bestanden daadwerkelijk zijn verwijderd.

### Verwijder Optioneel de Gerelateerde Databasetabellen

Controleer je database en verwijder eventuele tabellen die door de extensie zijn aangemaakt. Om het upgradeproces naar nieuwe versies te vergemakkelijken, verwijderen veel de-installatiescripts geen gerelateerde databasetabellen. Je kunt de lijst met tabellen in elk XML-bestand van de extensie vinden.

Als je van plan bent om een veiligere, compatibele versie van dezelfde extensie te installeren en je bestaande gegevens opnieuw wilt gebruiken, kun je de databasetabellen meestal zo laten.

### Verwijder Menulinks

Het eenvoudig verwijderen van de menulinks naar een extensie, of het niet publiceren van een module is **niet** genoeg om je site te beschermen! Zolang de bestanden van de extensie op je server aanwezig zijn, ben je kwetsbaar. Let op hoe in de volgende voorbeelden een aanvaller het Joomla! indexbestand kan omzeilen om direct elk bestand van elke extensie te benaderen.

```
    www.jouw_site.org/components/com_bad_component/vulnerable_file.php
    www.jouw_site.org/modules/mod_bad_module/vulnerable_file.php
```

*Vertaald door openai.com*

