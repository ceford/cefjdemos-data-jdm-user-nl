<!-- Filename: J4.x:Article_Tables / Display title: Artikel: Bewerken - Tabellen  -->

## Over Tabellen

In HTML bestaan tabellen uit rijen en kolommen van cellen. Een eenvoudige tabel kan bijvoorbeeld uit 4 rijen en 4 kolommen bestaan, wat 16 cellen oplevert. Cellen kunnen echter horizontaal of verticaal worden gecombineerd om behoorlijk ingewikkelde tabelstructuren te maken. Tabellen hebben ook minder voor de hand liggende functies zoals een kop, lichaam, voettekst en bijschriften. Tabellen kunnen genest worden!

Standaard breiden tabelcellen zich uit om hun inhoud te accommoderen. De enige opmaak komt van de tabelmarkup: standaard hebben kopcellen (`<th>`) vetgedrukte, gecentreerde tekst, terwijl gegevenscellen (`<td>`) normale, links uitgelijnde tekst hebben.

Tabellen zouden gereserveerd moeten worden voor strikt tabulaire gegevens, zoals een rooster of een kalender, waar het belangrijk is om de rij- en kolomstructuur te behouden. Tabellen dienen niet gebruikt te worden voor lay-out, zoals het plaatsen van afbeeldingen of tekst naast elkaar.

Er is meer informatie in de volgende artikelen:

- [Basis Tabellen](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)
- [Geavanceerde Functies en Toegankelijkheid](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Advanced)
- [Tabellen Stylen](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Styling_tables)

Tabellen zijn een dilemma! Als je een tabel invoegt met behulp van de TinyMCE-tabelhulpmiddelen, ziet de tabel er goed uit op het bewerkingsscherm en de site, maar de lay-out wordt bereikt met inline css-stijlen die omvangrijk en moeilijk te bewerken kunnen zijn. Als de tabel wordt ingevoegd als pure html ziet het resultaat er in de TinyMCE-teksteditor niet goed uit, maar kan het profiteren van Bootstrap-classes en er veel beter uitzien op de site. Beide methoden worden hieronder behandeld.

## Tabel Invoegen met TinyMCE-tools

Om te beginnen met een tabel:

- Open het artikel dat u wilt bewerken.
- Plaats de cursor op een lege regel waar de tabel moet verschijnen.
- Selecteer de knop *Tabel* in de eerste rij van de TinyMCE-tools.
- Selecteer in het vervolgkeuzemenu Tabel en beweeg vervolgens de cursor om het aantal rijen en kolommen te definiëren. De pijltjestoetsen werken hier ook voor.
- Selecteer de laatste cel in de 4x4 matrix.
- Vul de tabelcellen in.

Bewerkingsopties:

- U kunt een rij boven of onder een geselecteerde cel invoegen.
- U kunt een kolom voor of na een geselecteerde cel invoegen.
- U kunt een rij of kolom verwijderen.
- U kunt kolomgrenzen slepen om kolombreedtes of hoogtes te wijzigen.
- U kunt cellen samenvoegen - sleep over de cellen om ze te selecteren en gebruik vervolgens Tabel -> Cel -> Cellen samenvoegen.
- U kunt Tabeleigenschappen selecteren, inclusief randbreedte, stijl en kleur en achtergrondkleur.

Als u de Editor Wisselen-knop gebruikt, ziet u dat de lay-out wordt bereikt met inline-stijlverklaringen op elke rij en elke cel. Hier is een kort voorbeeld:

```html
<table style="border-collapse: collapse; width: 100%; height: 96px;" border="1"><colgroup><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"></colgroup>
<tbody>
<tr style="height: 24px;">
<td style="height: 24px;">Dag</td>
<td style="height: 24px;">Ochtend</td>
<td style="height: 24px;">Middag</td>
<td style="height: 24px;">Avond</td>
</tr>
<tr style="height: 24px;">
<td style="height: 24px;">Dinsdag</td>
<td style="height: 24px;">Welkom</td>
<td style="height: 24px;">Presentaties</td>
<td style="height: 24px;">BBQ</td>
</tr>
...
</tbody>
</table>
```

## Een Tabel Invoegen als HTML

Als je dat liever hebt, kun je inline stijlen achterwege laten en Bootstrap classes gebruiken. Dan zou je de tabel die door TinyMCE Table tools is gemaakt moeten aanpassen of zelf typen. Het zou er als volgt uitzien:

```html
<div class="table-responsive">
<table class="table table-striped table-bordered table-group-divider">
<thead>
<tr>
<th>Dag</th>
<th>Ochtend</th>
<th>Middag</th>
<th>Avond</th>
</tr>
</thead>
<tbody class="table-group-divider">
<tr>
<th>Dinsdag</th>
<td>Welkom</td>
<td>Presentaties</td>
<td>BBQ</td>
</tr>
...
</tbody>
</table>
</div>
```

Hier hebben de Bootstrap classes de volgende effecten:

- `table` - past verschillende stijlen toe voor een mooie standaard tafelindeling.
- `table-striped` - wisselrijen zijn donker en licht.
- `table-bordered` - past grenzen toe aan de cellen.
- `table-group-divider` - past een dikke lijn boven een element toe.
- `table-responsive` - maakt het mogelijk een brede tabel naar rechts en links te scrollen.

De volgende sitescreenshot toont een tabel voor een conferentieprogramma met de standaard inline stijlen van TinyMCE en een vergelijkbare tabel met Bootstrap stijlen:

![Voorbeeldtabellen](../../../en/images/articles/articles-site-tables.png)

Bekijk de Bootstrap documentatie over [Tabellen](https://getbootstrap.com/docs/5.3/content/tables/) voor meer opties.

## Nabeschouwing

Je zou de HTML voor een tabel in een Aangepaste module kunnen plaatsen en die module in het artikel kunnen opnemen. In het artikel verschijnt dat als `{loadmoduleid xx}`, waarbij xx de module-id is.

*Vertaald door openai.com*

