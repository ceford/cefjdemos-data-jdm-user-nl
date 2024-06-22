<!-- Filename: J3.x:Update_fails_with_an_error_message / Display title: Update mislukt met een foutmelding -->

Joomla!  3.6.1

## Gerapporteerde fouten

Wanneer de website wordt geüpdatet naar Joomla! 3.6.1 door gebruik te
maken van de ingebouwde Joomla! Update extensie, zal de volgende
foutmelding verschijnen: <img
src="https://docs.joomla.org/images/9/98/Joomla-3.6.1-error-message-nl.png"
decoding="async" data-file-width="820" data-file-height="31" width="820"
height="31" alt="Joomla-3.6.1-error-message-nl.png" />

## Getroffen versies

Algemene informatie

Dit heeft alleen betrekking op de Joomla! versie(s): **3.6.1**

## Wat is de oorzaak?

3.6.1 introduceert een CSRF token check in de update component als extra
beveiligingsniveau. 3.6.0 tot 2.5.4 (iedere versie met de update
component) zullen vastlopen op de CSRF token, omdat deze versies de
benodigde code niet genereren als controle. Toekomstige updates zullen
wel correct werken.

## Hoe op te lossen

### Updaten van Joomla! 3.6.0

- Ga terug naar het controlepaneel in het beheergedeelte
  `example.com/administrator`
- Ga vervolgens naar Extensies  **→**  Beheren  **→**  Database
- Een bericht dat de database niet up-to-date is wordt weergegeven
- Klik op de knop Repareren in de werkbalk.

### Updaten van Joomla! LAGER dan 3.6.0

Als u werkt met een versie lager dan 3.6.0:  

- Update eerst naar Joomla! 3.6.0 en **NIET** direct naar Joomla!
  3.6.1  
- Update `com_joomlaupdate` via extensiebeheer  
- en voer vervolgens de update van Joomla! 3.6.0 naar Joomla! 3.6.1 uit.

Er is een nieuwe versie voor `com_joomlaupdate` beschikbaar in het
beheergedeelte via update in extensiebeheer.

Voor meer informatie

Bekijk de officiële aankondiging gerelateerd aan het probleem <a
href="https://www.joomla.org/announcements/release-news/5666-the-joomla-3-6-1-update.html"
class="external text" target="_blank" rel="noreferrer noopener">HIER</a>

**Opmerking**: Als uw website PHP 5.3 gebruikt, kan deze foutmelding
getoond worden bij een poging om in te loggen:  
` 0 Failed to start the session: already started by PHP ($_SESSION is set).`  
Joomla! 3.6.2 verhelpt dit probleem. Zie
<a href="https://github.com/joomla/joomla-cms/pull/11430"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Fix logging in in PHP 5.3</a>.
