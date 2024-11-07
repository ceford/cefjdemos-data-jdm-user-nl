<!-- Filename: J4.x:Assorted_Issues / Display title: Diverse Zaken   -->

## Probleem met Omleiding na Upgrade naar 4.0.6

Dat is een bug! Regel 243 van *plugins/system/redirect/redirect.php*:

       $db->updateObject('#__redirect_links', $redirect, 'id');

moet zijn

       $this->db->updateObject('#__redirect_links', $redirect, 'id');

## Een pagina wordt weergegeven zonder opmaak

Mogelijke oorzaak: Een gzip-sectie in *.htaccess* comprimeert de
reeds-gecomprimeerde CSS- en JavaScript-bestanden.

Zie dit gedeelte van het *.htaccess* bestand:

    ## Deze directieven zijn alleen ingeschakeld als de Apache mod_headers-module is ingeschakeld.
    ## Dit gedeelte controleert of er een .gz-bestand bestaat en als dat zo is, zal het
    ##     het direct streamen of terugvallen om elk bestand snel te gzippen
    ## Als je site er vreemd uitziet na het inschakelen hiervan, en je ziet
    ##     ERR_CONTENT_DECODING_FAILED in het netwerk-tabblad van je browserconsole,
    ##     dan comprimeert je server al css- en js-bestanden en heb je deze
    ##     blok niet nodig in je .htaccess-bestand

    ...

Als dit aanwezig is, commentarieer het uit of verwijder het.

## De lijst met site-modules is leeg

Mogelijke oorzaak: de MySQL-sorteerbuffer is mogelijk te klein.

Ga met phpMyAdmin naar **Home**→**Variabelen**→**Sorteerbuffer grootte**.

Deze moet ten minste 256K zijn en bij voorkeur 512K. Bij sommige shared hostingdiensten kan deze zijn ingesteld op 128K. Vraag de hostingdienst om dit te verhogen.

## Update Fout na Updaten naar 4.0.4

Oorzaak: een essentiële wijziging in de updateprocedure die een klein aantal gebruikers beïnvloedt.

Kijk in *.htaccess* voor deze regel:

    RewriteRule ^administrator/components/com_joomlaupdate/restore\.php$ - [L]

Verander dit in:

    RewriteRule ^administrator\/components\/com_joomlaupdate\/extract\.php$ - [L]

Voor meer informatie, zie:

<a
href="https://www.joomla.org/announcements/release-news/5850-changes-to-update-process-that-you-need-to-be-aware-of.html"
rel="noreferrer noopener">Wijzigingen
in het Updateproces waar je van op de hoogte moet zijn</a>

## Artikelen Zichtbaar in Database en Frontend maar Niet Zichtbaar in Backend

Dit gebeurt wanneer artikelen direct in de database worden geïmporteerd, wat prima werkte in Joomla 3, maar niet in Joomla 4. De oplossing van een gebruiker is als volgt:

    Ik importeerde artikelen direct in de database in de #__content tabel zoals ik vaak deed in Joomla 3.
    Echter, in Joomla 4 waren ze niet zichtbaar.

    In Inhoud > Categorieën, telden de categorie-itemtellers de geïmporteerde artikelen.
    Maar ze waren niet zichtbaar in Inhoud > Artikelen.

    Ik loste het op door de nodige verwijzingen in de #__workflow_associations tabel te creëren voor elk geïmporteerd artikel:
    item_id = artikel ID, stage_id = 1 en extension = com_content.article.

Met dit van een andere gebruiker:

Deze query zou het voor je moeten doen. Vervang \#\_\_ door je eigen databaseprefix.

Deze query voorkomt dubbele items in de workflow-associatietabel

    INSERT INTO #__workflow_associations (item_id, stage_id, extension)
    SELECT c.id as item_id, '1', 'com_content.article' FROM #__content AS c
    WHERE NOT EXISTS (SELECT wa.item_id FROM #__workflow_associations AS wa WHERE wa.item_id = c.id);

*Vertaald door openai.com*

