<!-- Filename: Verifying_permissions / Display title: Bestandsrechten: Linux -->

## Inleiding

De volgende informatie is voor op Linux gebaseerde servers. Als je webserver een Microsoft Windows-gebaseerde server (IIS) is, moet je [Permissies: Windows](jdocmanual?article=user/test-installations/permissions-windows) raadplegen.

Afhankelijk van de beveiligingsconfiguratie van je webserver zijn de aanbevolen standaardpermissies:

- 755 voor mappen
- 644 voor bestanden
- 444 voor het bestand `configuration.php` (wanneer een Globale Configuratiewijziging wordt opgeslagen, verandert Joomla eerst de rechten naar 644, slaat de wijziging op en verandert vervolgens de rechten terug naar 444)

<div class="alert alert-warning">
Waarschuwing!

Gebruik nooit 777 tenzij je precies weet wat je doet! Gebruik geen extensies die 777-permissies vereisen!
</div>

## Hoe de Machtigingen te Lokaliseren

Er zijn verschillende methoden beschikbaar om de machtigingen van websitebestanden of -mappen te bekijken en te wijzigen. De bestandsverkenner van het hostbesturingspaneel of een gebruikelijk [File Transfer Protocol (FTP)](https://en.wikipedia.org/wiki/File_Transfer_Protocol) programma zou een methode moeten bieden om bestands- en mapmachtigingen te zien en te wijzigen. De opdrachtregel is goed voor degenen die toegang hebben tot de terminal en vertrouwd zijn met systeemopdrachten.

Afhankelijk van wat je gebruikt, zou je iets moeten zien zoals deze afbeelding van een deel van het Joomla-hoofdbestandensysteem zoals te zien in cPanel:

![machtigingen verifiëren in cpanel](../../../en/images/test-installations/verifying-permissions-cpanel.png)

De machtigingen bevinden zich helemaal rechts en worden voorafgegaan door een nul om aan te geven dat het octale getallen zijn. Er zou een formulier moeten zijn om de machtigingen van een of meer geselecteerde items te wijzigen:

![machtigingen wijzigen in cpanel](../../../en/images/test-installations/verifying-permissions-cpanel-change.png)

In een terminalvenster worden bestand- en mapmachtigingen weergegeven als lettergroepen in plaats van als cijfers (de voorloop `d` geeft aan dat het item een directory is):

```sh
drwxr-xr-x   20 ceford  staff     640 14 Oct 22:23 components
-r--r--r--    1 ceford  staff    3485 27 Oct 06:56 configuration.php
drwxr-xr-x    2 ceford  staff      64 20 Oct 14:21 files
-rw-r--r--    1 ceford  staff    6899 30 Sep 09:27 htaccess.txt
drwxr-xr-x   15 ceford  staff     480 24 Oct 12:19 images
```

## Permissie Nummers

In een permissieweergave in de vorm van 777, komt elk octaal cijfer overeen met drie letters voor drie verschillende gebruikersgroepen:

- Eerste cijfer = eigenaar (de eigenaar van het item - `ceford` in de bovenstaande commandoregel lijst)
- Tweede cijfer = groep (de groep die toegang heeft - `staff` in de bovenstaande lijst)
- Derde cijfer = anderen (iedereen anders op deze computer)

## Betekenis van de nummers

Elk octaal cijfer is de som van de verleende permissies:
```sh
     r = Lezen   = 4
     w = Schrijven = 2
     x = Uitvoeren = 1
```
Tel de nummers op voor elke vereiste permissie voor een gegeven gebruikersgroep:

| "Octaal" \# | (r)ead | (w)rite | e(x)ecute | Gebruiker of Groep of Anderen |
|-------------|--------|---------|-----------|------------------------------|
| 0           | nee    | nee     | nee       | `---` 0+0+0 = 0              |
| 1           | nee    | nee     | ja        | `--x` 0+0+1 = 1              |
| 2           | nee    | ja      | nee       | `-w-` 0+2+0 = 2              |
| 3           | nee    | ja      | ja        | `-wx` 0+2+1 = 3              |
| 4           | ja     | nee     | nee       | `r--` 4+0+0 = 4              |
| 5           | ja     | nee     | ja        | `r-x` 4+0+1 = 5              |
| 6           | ja     | ja      | nee       | `rw-` 4+2+0 = 6              |
| 7           | ja     | ja      | ja        | `rwx` 4+2+1 = 7              |


## Voorbeelden

- 755 is rwx (eigenaar), r-x (groep) en r-x (anderen) of met andere woorden iedereen mag lezen en uitvoeren (runnen) maar alleen de eigenaar (jij) mag wijzigingen aanbrengen in het bestand. Het zou er zo uitzien wanneer het allemaal samen wordt gevoegd: `-rwxr-xr-x`. Dit is de normale instelling voor mappen.
- 644 is rw-, r--, r-- of IEDEREEN kan het bestand lezen maar alleen de eigenaar mag naar het bestand schrijven of `-rw-r--r--`. Dit is de normale instelling voor bestanden.
- 777 of `-rwxrwxrwx` betekent dat IEDEREEN lezen, schrijven en uitvoeren kan op ELK bestand
  <div class="alert alert-warning">
  Dit is iets wat je **NOOIT** wilt toestaan op je server/website, tenzij je er absoluut zeker van bent dat je weet wat je doet.
  </div>

Permissies worden gebruikt voor zowel mappen als bestanden, daarom kun je dit `drwxr-xr-x` zien waar de `d` voor directory staat.

Voor een volledige uitleg lees het Wikipedia-artikel over [Filesystem permissies](https://en.wikipedia.org/wiki/Filesystem_permissions)

*Vertaald door openai.com*

