<!-- Filename: J4.x:Updating_from_an_existing_version / Display title: Versie-update  -->

## Introductie

**Onthoud: Maak altijd een back-up van je site voordat je gaat updaten.**

De aanbevolen manier om installaties van Joomla! bij te werken, is door de *Joomla Update Component* te gebruiken.

Een standaardinstallatie van Joomla 4 en later bevat een nuttig meldingspaneel op het startdashboard na inloggen. Je kunt in één oogopslag zien of er een update beschikbaar is en het versienummer bekijken.

Het updatebericht dat in het meldingenpaneel verschijnt, is afhankelijk van het *Updatekanaal* dat is ingesteld op de pagina *Joomla Update: Opties* en de huidige *Kleine* versie. Met **Updatekanaal** ingesteld op **Standaard** worden updates binnen de huidige *Grote* versie gemeld. Met de parameter ingesteld op *Joomla Next* kun je updaten naar de nieuwste huidige versie en vervolgens op de knop **Controleren op updates** klikken om te zien of de volgende *Grote* versie beschikbaar is.

Hoewel Joomla je zal informeren wanneer er een update beschikbaar is, vereist het dat jij de update uitvoert. Het is een eenvoudig proces dat zo snel mogelijk moet worden uitgevoerd om de site actueel te houden.

## Toegang tot de Update Component

Als het notificatiepaneel wordt weergegeven op het startdashboard, selecteer dan de knop **x.y.z Beschikbaar - Nu bijwerken!** om naar de Update Component te gaan.

![joomla update notificatie in startdashboard](../../../en/images/migration/version-update-notification-home-dashboard.png)

Als alternatief, om toegang te krijgen tot de Update Component via het Beheerdersmenu, selecteer **Systeem** om via het **Systeemdashboard** te gaan.

![joomla update notificatie in systeemdashboard](../../../en/images/migration/version-update-notification-system-dashboard.png)

Het systeemdashboard heeft een *Updatepaneel* dat een Joomla-link bevat die het beschikbare updateversienummer weergeeft. Selecteer de **Joomla**-link om naar de Update Component te gaan.

## Het Uitvoeren van de Update

Joomla! 4 en 5 bieden een Pre-Updatecontrole voor updates naar minor versies.
Deze weergave van de Joomla Update-component toont technische specificaties van
de server waarop de site zich bevindt en kern- en derde-partijextensies die de
Update Server gebruiken in lijstvorm.

**Let op:** Het *Pre-Updatecontrole*-scherm wordt niet weergegeven als de site op de
huidige **Minor** versie is.

![joomla pre update controle](../../../en/images/migration/version-update-pre-update-check.png)

Let goed op de controle resultaten en neem maatregelen om eventuele problemen
die naar voren komen op te lossen voordat je bijwerkt. Mogelijk moet je incompatibele
extensies bijwerken, uitschakelen of deïnstalleren voordat je Joomla bijwerkt.

Het is niet ongebruikelijk om waarschuwingen voor *Aanbevolen Instellingen* te zien,
aangezien deze vaak server specifiek en hosting gerelateerd zijn. Het is waarschijnlijk
dat ze bestonden toen je Joomla installeerde en ze zullen hoogstwaarschijnlijk de
voltooiing van de update niet voorkomen.

*Let op de herinnering dat je sterk wordt aangeraden een back-up te maken als
je dat nog niet hebt gedaan!*

Er is een link onder de updateknop. In de meeste gevallen kun je deze link negeren.
Het biedt een optie om de updatebestanden handmatig te uploaden als
je server zich achter een firewall bevindt of anderszins niet in staat is om
contact te maken met de Joomla-update servers.

Wanneer je de Pre-Updatecontrole hebt doorgenomen en tevreden bent, selecteer je **Update**.

### Bevestigen van de Update

![start update pagina](../../../en/images/migration/version-update-start-update.png)

Klik op het selectievakje om te bevestigen dat je een back-up hebt gemaakt en hebt
gecontroleerd of extensies compatibel zijn, klik daarna op **Start Update**.

### Update Voortgang

![update voortgang pagina](../../../en/images/migration/version-update-progress.png)

Zodra de update start, verschijnt er een voortgangsbalk terwijl de Joomla-bestanden
worden bijgewerkt.

### Voltooiing

![update voltooiingspagina](../../../en/images/migration/version-update-completion.png)

Wanneer de voortgangsbalk 100% bereikt, zal een systeembericht bevestigen dat je
site is bijgewerkt en het versienummer weergeven. Het versienummer wordt ook
bijgewerkt in de bovenste werkbalk, naast de sitenaam.

Klik op de **Terug**-knop en je wordt teruggeleid naar de Joomla Update
Component waar je opnieuw kunt controleren op updates.

## Controle na update

Zodra de update is voltooid, moet je enkele controles uitvoeren om er zeker van te zijn dat alles naar verwachting is verlopen, dat er geen fouten aanwezig zijn en dat er geen wijzigingen zijn die verdere actie vereisen.

### Frontend-controle

Ga naar de frontend van de website en controleer of deze werkt en wordt weergegeven zoals vóór de update. Gebruik de combinatie *Shift + Herladen* om je browser te dwingen eventuele wijzigingen in stylesheets en scripts opnieuw te laden.

### Systeemcontroles

Selecteer **Systeem** in het zijbalkmenu om naar het Systeemdashboard te gaan. Dit geeft je een overzicht van de huidige status van je Joomla-site.

![systeemdashboard na update](../../../en/images/migration/version-update-after-update.png)

In dit voorbeeld kunnen we zien dat er sinds de update twee items zijn die aandacht vereisen. Ze zijn gemarkeerd met een label dat een aantal bevat. Het aantal geeft aan hoeveel items aandacht vereisen. Door op elk item te klikken, kun je ze corrigeren.

**Opmerking** Het Systeemdashboard voert een controle uit elke keer dat de pagina wordt geladen. Houd er rekening mee dat de cache-instellingen van de browser dit kunnen beïnvloeden. Het is een goede gewoonte om de cache van de browser te wissen wanneer je controleert met *Shift + Herladen*.

### Databasecontrole

Navigeer naar **Systeem → Onderhoud → Database**. Als je database up-to-date is, zou je een scherm moeten zien dat lijkt op het onderstaande:

![databasecontrole na update zonder problemen](../../../en/images/migration/version-update-after-update-database-check-no-problems.png)

Als je database niet up-to-date is, zie je een scherm met een lijst van de gevonden problemen, zoals het onderstaande:

![databasecontrole na update met problemen](../../../en/images/migration/version-update-after-update-database-check-problems.png)

Selecteer in dit geval de probleem extensie *Naam* en vervolgens de Update Structure knop in de werkbalk. Joomla zal je database bijwerken om de vermelde problemen te corrigeren en vervolgens het scherm opnieuw weergeven. Als de correctie succesvol was, geeft de weergave aan dat de database up-to-date is.

**Opmerking:** Als er nog steeds fouten bestaan, zorg ervoor dat alle databasetabellen zijn ingecheckt.

## Systeem Ontdekken

In sommige gevallen, wanneer je naar een nieuwe Joomla-versie updatet, worden er nieuwe kernextensies toegevoegd. Als er problemen waren met de database-update, zijn deze extensies mogelijk niet correct geïnstalleerd. Om dit te controleren, navigeer naar **Systeem → Ontdekken**. Selecteer vervolgens het Ontdekkensymbool in de werkbalk. Het scherm zou er als volgt uit moeten zien:

![Ontdekkenscherm Zonder Extensies Om Te Installeren](../../../en/images/migration/version-update-after-update-discover.png)

Als dat zo is, weet je dat alle nieuwe extensies die tijdens de update zijn toegevoegd correct in de database zijn geïnstalleerd.

Als er niet-geïnstalleerde extensies zijn, zullen ze vergelijkbaar met het volgende scherm worden weergegeven:

![Ontdekkenscherm Met Ontdekte Extensies Om Te Installeren](../../../en/images/migration/version-update-after-update-discover-found.png)

In dit geval vink je de vakjes aan en klik je op het Installeren-symbool in de werkbalk. Joomla zal de extensie(s) installeren en vervolgens het scherm weergeven waarop geen ontdekte extensies staan. Op dit punt zijn de nieuwe extensies in de database geïnstalleerd.

## Probleemoplossing

Als je vragen, problemen of fouten hebt vóór, tijdens of na de update, stel ze dan op het [Migreren en Upgraden naar Joomla! 4.x Forum](https://forum.joomla.org/viewforum.php?f=812).

Als je problemen of fouten ervaart tijdens het updateproces, hier zijn enkele tips.

- Wis de cache van je browser. Er kunnen wijzigingen zijn aangebracht aan de CSS of Javascript die na een update opnieuw door je webbrowser moeten worden geladen.
- Als er na de update foutmeldingen van de database verschijnen, controleer dan zeker de link **Systeem → Onderhouds paneel → Database**. In sommige gevallen, als er een databasefout optreedt, zal dit voorkomen dat alle database-updates worden uitgevoerd. In dat geval kun je ze uitvoeren via de Database link en vervolgens de methode **Systeem → Installeren → Ontdekken** gebruiken om te controleren en nieuwe extensies te installeren.
- Het updateproces maakt of voegt toe aan een logbestand genaamd administrator/logs/joomla_update.php, dat je kunt openen met een teksteditor om de stappen in het logboek te bekijken. Het zal de belangrijkste stappen weergeven (zip downloaden, installeren, SQL-instructies uitvoeren, opruimen), zoals dit:

```
2024-04-17T09:13:16+00:00    INFO 127.0.0.1    update    Update gestart door gebruiker Jimmy (139). Oude versie is 5.0.3.
2024-04-17T09:13:18+00:00    INFO 127.0.0.1    update    Downloaden van updatebestand van ...
2024-04-17T09:13:28+00:00    INFO 127.0.0.1    update    Bestand Joomla_5.1.0-Stable-Update_Package.zip gedownload.
2024-04-17T09:13:28+00:00    INFO 127.0.0.1    update    Start van installatie van nieuwe versie.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    Installatie afronden.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    Start van SQL-updates.
2024-04-17T09:13:40+00:00    INFO 127.0.0.1    update    De huidige databaseversie (schema) is 5.0.0-2023-09-11.
... Veel individuele SQL-query's
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    Einde van SQL-updates.
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    De-installeren van extensies
2024-04-17T09:13:41+00:00    INFO 127.0.0.1    update    Verwijderen van verwijderde bestanden en mappen.
2024-04-17T09:13:44+00:00    INFO 127.0.0.1    update    Opruimen na installatie.
2024-04-17T09:13:44+00:00    INFO 127.0.0.1    update    Update naar versie 5.1.0 is voltooid.
```

*Vertaald door openai.com*
