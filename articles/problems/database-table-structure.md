<!-- Filename: J4.x:Fix_%22Database_Table_Structure_NOT_Up_to_Date%22_before_Update / Display title: Databasetabelstructuur  -->

## Gerapporteerde Fouten

Bij het bijwerken van Joomla! moet de database tabelstructuur up-to-date zijn voordat het proces kan beginnen. De *Pre-Update Controle voor Joomla* klaagt als dit niet het geval is.

Maar wanneer je naar **Systeem → Onderhoud → Database** gaat, is er geen invoer beschikbaar. Dit werd gerapporteerd in verschillende Joomla! 4.x versies.

## Wat is de Oorzaak

Het probleem wordt veroorzaakt door een lege `#__schemas`-tabel in de database. Dit gebeurt waarschijnlijk wanneer de Joomla!-instantie niet is geïnstalleerd via de officiële Joomla!-installer, maar door middel van een aangepast script dat niet alle vereiste gegevens heeft ingevuld.

## Hoe te Repareren

Je kunt dit oplossen door de ontbrekende waarde aan de tabel toe te voegen. Gebruik phpMyAdmin (of een andere databaseclient), ga naar de tabel `#__extensions`. Zoek naar name='files_joomla' en noteer de extension_id (in ons geval *211*).

Vervolgens moet je weten welk het nieuwste SQL-script is dat is geïnstalleerd. Ga naar `administrator/components/com_admin/sql/updates/mysql` en zoek de bestandsnaam met de hoogste versie. In dit voorbeeld gaan we ervan uit dat *4.0.3-2021-09-05.sql* de bestandsnaam is met de hoogste versie. Nu moet je dit toevoegen in je insert query als de tweede waarde:

```sql
INSERT INTO `#__schemas` (`extension_id`, `version_id`) VALUES
(211, '4.0.3-2021-09-05');
```

of voor PostgreSQL:

```sql
INSERT INTO "#__schemas" ("extension_id", "version_id") VALUES
(211, '4.0.3-2021-09-05');
```

Vervang `#__` door je database prefix voordat je de statements uitvoert.

Ga vervolgens vanuit het Administrator-menu naar **Systeem → Onderhoud → Database** en herstel de tabellen.

Nu zou de update naar verwachting moeten werken.

*Vertaald door openai.com*

