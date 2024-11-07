<!-- Filename: J4.x:Article_Check-out_and_Check-in / Display title: Artikel: Inchecken  -->

## Inleiding

Veel Joomla-websites hebben meerdere gebruikers die toestemming hebben om artikelen te bewerken. Om te voorkomen dat twee gebruikers tegelijkertijd proberen hetzelfde artikel te bewerken, heeft elk artikel een **checked_out** databaseveld om aan te geven of het in gebruik is. Dit wordt ingesteld wanneer een artikel wordt geopend voor bewerking en wordt gewist wanneer het bewerkingsformulier wordt gesloten met behulp van de knoppen *Opslaan & Sluiten* of *Sluiten*.

Soms wordt een artikelbewerking niet correct afgesloten, bijvoorbeeld door de terugknop van de browser te gebruiken of doordat de gebruikerssessie verloopt. In dat geval blijft het checked_out veld ingesteld. Dit wordt in artikeloverzichten weergegeven met een klein hangslotpictogram. Het hangslotpictogram is ook te zien waar normaal gesproken een bewerkingslink zou staan wanneer men is ingelogd op de frontend van de site.

Om de normale werking te herstellen, moeten uitgecheckte items worden ingecheckt.

## Artikel Inchecken

Er zijn verschillende methoden beschikbaar om een artikel in te checken.

- Als jij de laatste persoon was die het artikel heeft bewerkt, kun je het artikel bewerken vanuit de backend of frontend zonder dat je hoeft in te checken.
- Neem contact op met de laatste persoon die het artikel heeft bewerkt om te zien of zij klaar zijn met bewerken. Je kunt de cursor boven het hangslot houden en de tooltip-popup zal de naam weergeven van de gebruiker die het artikel heeft uitgecheckt.
- Als je een Super User of Administrator bent, kun je het hangslotpictogram selecteren om dit ene item in te checken.
- Je kunt ook meerdere artikelen selecteren en de optie *Inchecken* gebruiken vanuit de knop *Acties* in de werkbalk.
- Als je het item niet zelf kunt inchecken, vraag dan een Super User of Administrator om het te doen.

## Globale Check-in

Als je een Super User of Administrator bent, kun je de Globale Check-in
functionaliteit gebruiken om items te selecteren die ingecheckt moeten worden.

Deze functionaliteit moet met grote voorzichtigheid gebruikt worden, vooral in
omgevingen met meerdere gebruikers. Het checkt alle eerder uitgecheckte items in,
ongeacht of jij ze uitgecheckt hebt of niet. Een mogelijk ongewenst neveneffect
kan zijn dat meerdere redacteuren aan hetzelfde document werken. In dit geval
wordt de versie van degene die als laatste op de opslaan-knop klikt als
de definitieve versie opgeslagen.

Je moet je er ook van bewust zijn dat veel andere extensies **checked_out**
velden hebben. Bijvoorbeeld kunnen modules en categorieën voor
bewerking uitgecheckt en per ongeluk in die staat achtergelaten worden.

Vanuit het Administrator-menu:

- Selecteer **Home Dashboard → Globale Check-in** of
  **Systeem → Onderhoudspaneel → Globale Check-in**.
- De lijst toont het aantal uitgecheckte items.

![Pagina voor globale check-in](../../../en/images/articles/global-checkin.png)

- Selecteer in de lijst van databastabellen het selectievakje voor het type
  item dat ingecheckt moet worden.
- Selecteer *Check-in* vanuit de Werkbalk.

Alle uitgecheckte items in die tabel worden ingecheckt.

## Tabellen met checked_out-veld

Je kunt achterhalen welke tabellen een checked_out-kolom hebben met deze query in phpMyAdmin:

    SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('checked_out') AND TABLE_SCHEMA='j423sd';

En het resultaat zou er zo uit moeten zien:

    TABLE_NAME
    bi2hb_banner_clients
    bi2hb_banners
    bi2hb_categories
    bi2hb_contact_details
    bi2hb_content
    bi2hb_extensions
    bi2hb_fields
    bi2hb_fields_groups
    bi2hb_finder_filters
    bi2hb_menu
    bi2hb_modules
    bi2hb_newsfeeds
    bi2hb_scheduler_tasks
    bi2hb_tags
    bi2hb_update_sites
    bi2hb_user_notes
    bi2hb_workflow_stages
    bi2hb_workflow_transitions
    bi2hb_workflows

*Vertaald door openai.com*  

