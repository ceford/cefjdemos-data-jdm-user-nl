<!-- Filename: Installing_an_extension / Display title: Installeren van een extensie -->

Voordat u begint is het altijd verstandig om de documentatie die bij de
extensie hoort door te lezen. De meeste extensies hebben een website en
forum, en het is een goed idee deze eerst te bekijken. Wanneer de
extensie een README bestand bevat moet u deze eerst lezen.

De procedure zal voor de meeste extensies en gebruikers de volgende
zijn:

- Download de extension als zipbestand naar uw computer.
- Vanaf het beheergedeelte van uw Joomla website (administratie)
  selecteert u Extensies  **→**  Installeren/Deïnstalleren.
- Klik op de knop bladeren en selecteer het extensiepakket op uw
  computer.
- Klik op de knop Click the Uploaden & installeren.
- Sommige extensies kunnen verdere instructies geven tijdens de
  installatie.
- Let op dat modules en plugins ingeschakeld moeten worden voordat ze
  werken.

Er zijn enkele situaties waarin deze procedure niet werkt.

Soms moet het zipbestand lokaal uitgepakt worden voorafgaand aan de
installatie. Dit is in de meeste gevallen de oplossing voor de
foutmelding dat het bestand niet het juiste format heeft. Probeer na het
uitpakken de individuele items te installeren. Denk erom dat de
geüploade bestanden die u wilt installeren nog steeds gezipt moeten
zijn.

Soms lukt het niet om extensies via de automatische manier te
installeren. Bijvoorbeeld erg grote extensies die de maximum
uploadgrootte ingesteld door uw host overschrijdt.

Ook is het mogelijk dat u de volgende foutmelding ziet:

    Warning: is_dir() [function.is-dir]: open_basedir restriction in effect. File(/) is not within the allowed path(s): ...

dit is het gevolg van een beperking van uw webhost waardoor Joomla! niet
kan controleren of de basismap bestaat. In dit geval kunt u niet gebruik
maken van de automatische installatie.

## Handmatige installatie

Pak eerst alle bestanden uit in een lokale map (bijvoorbeeld
`com_installer`). Stuur vervolgens de map (met behulp van FTP) naar een
map onder de geïnstalleerde map (bijvoorbeeld
`administrator/components`), geschikt voor het type extensie die u
installeert (zichtbaar in zijn xml bestand, een regel zoals

). Gebruik daarna de installer, maar selecteer "installeer vanuit map"
welke de juiste mapnaam aangeeft. Deze mapnaam moet een absoluut pad
hebben vanaf de root van het bestandssysteem.
