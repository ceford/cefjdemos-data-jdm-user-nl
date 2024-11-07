<!-- Filename: Setting_up_automatic_Smart_Search_indexing / Display title: Slimme Zoekindexering  -->

## Automatisch Indexeren

Hoewel de Smart Search-index automatisch up-to-date wordt gehouden wanneer inhouditems worden gewijzigd, zijn er enkele omstandigheden waarin je de indexer opnieuw moet uitvoeren. Dit kun je handmatig doen via de Index-toolbarknop op de Smart Search: Geïndexeerde Inhoud-pagina. Als je echter de inhoud automatisch opnieuw moet indexeren, is het ook mogelijk om de indexer vanaf de opdrachtregel uit te voeren. Dit is bijzonder handig om de indexer vanuit een *cron*-taak uit te voeren.

Vanaf de cli-directory is de opdrachtregel:

```
php joomla.php finder:index
```

Typische uitvoer van de opdrachtregel-indexer ziet er als volgt uit:

    Smart Search INDEXER
    ============================

    Starten van de Indexer
    Opzetten van Finder-plugins
    154 items ingesteld in 0.094 seconden.
     * Batch 1 verwerkt in 0.213 seconden.
     * Batch 2 verwerkt in 0.182 seconden.
     * Batch 3 verwerkt in 0.177 seconden.
     * Batch 4 verwerkt in 0.009 seconden.
    Totale verwerkingstijd: 0.676 seconden.

## Opschonen Voor Indexeren

Normaal gesproken voert de indexeerder een incrementele update van de index uit. Dat wil zeggen, het zal alleen de index bijwerken voor die inhoudselementen die zijn gewijzigd sinds de index voor het laatst is bijgewerkt. Als je echter alle bestaande indexvermeldingen volledig moet wissen voordat je de index helemaal opnieuw opbouwt, dan moet je een "opschonen en dan indexeren" operatie uitvoeren. Om dat te doen, kun je het `--purge` argument toevoegen aan de opdrachtregel, zoals dit:

    php joomla.php finder:index --purge

Let op dat dit zal proberen om eventuele statische filters die je mogelijk hebt ingesteld te behouden, terwijl het klikken op de "Opschonen" werkbalkknop in de beheerder **niet** je statische filters zal behouden.

## Een *cron* taak instellen

Hoewel de details buiten het bereik van dit artikel vallen, moet je over het algemeen gewoon het bovenstaande commando invoeren in de *cron* taakmanager en de tijd of tijden specificeren waarop de taak moet worden uitgevoerd. Waarschijnlijk moet je het volledige pad naar de indexer opnemen. Bijvoorbeeld, als volgt:

    php /var/www/myjoomla/cli/joomla.php finder:index -- purge

En mogelijk het volledige pad naar het php-bestand zoals `/usr/local/opt/php@8.2/bin/php`.

## Geheugenproblemen

Als uw site bijzonder complexe indexeringseisen heeft, is het mogelijk
dat de standaard geheugentoewijzing niet voldoende is voor de indexeerder
om voltooid te worden. U kunt het geheugen dat is toegewezen aan de
opdrachtregel-indexeerder vergroten door een extra parameter op de
opdrachtregel toe te voegen, zoals dit:

    php -d memory_limit=256M joomla.php finder:index

Vervang de `256M` door wat het meest geschikt is voor uw situatie.

De opdrachtregel-indexeerder gebruikt dezelfde parameters als de indexeerder op de
Smart Search: Geïndexeerde Inhoud-pagina. U kunt de parameters wijzigen met behulp van de
Opties werkbalkknop op die pagina. Merk op dat zowel de velden
**Batchgrootte van de indexeerder** als **Limiet geheugentabel** van invloed zijn op de hoeveelheid
geheugen die wordt gebruikt door de indexeerder.

*Vertaald door openai.com*

