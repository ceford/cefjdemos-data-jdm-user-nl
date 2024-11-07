<!-- Filename: J4.x:Apache_PHP_Handler / Display title: Apache PHP-handlers  -->

## Notities

Om te bepalen welke methode je webserver gebruikt om php-bestanden af te handelen, gebruik de **Administrator / System / System Information** links en selecteer het PHP-informatie tabblad. Zoek op de pagina naar **Server API**. De gebruikelijke manieren waarop een Apache-webserver PHP-bestanden afhandelt, zijn onder andere:

### DSO (mod_php)

- **Voordeel:** een van de snelste handlers die beschikbaar is.
- **Nadeel:** werkt alleen met een enkele versie van PHP; bestanden die door php-scripts worden opgeslagen, zijn eigendom van de Apache-gebruiker **behalve** wanneer ze worden gebruikt in combinatie met mod_ruid2.
- **Te herkennen aan:** Server API - Apache 2.0 Handler

### CGI/FastCGI

- **Voordeel:** scripts worden uitgevoerd als de domein- of subdomeingebruiker, zeer snelle handler.
- **Nadeel:** langzamer dan mod_php, je kunt geen PHP-configuratiewijzigingen aanbrengen in een .htaccess-bestand.
- **Te herkennen aan:** Server API - CGI/FastCGI

### FPM/FastCGI

- **Voordeel:** zeer snel, extra niveau van flexibiliteit.
- **Nadeel:** gebruikt meer geheugen dan de meeste anderen, je kunt geen PHP-configuratiewijzigingen aanbrengen in een .htaccess-bestand.
- **Te herkennen aan:** Server API - FPM/FastCGI

### LSAPI (mod_lsapi)

- **Voordelen:**
   - Biedt ondersteuning voor caching.
   - Het is de meest performante handler met een laag geheugengebruik.
   - Geen configuratie vereist.
   - Het kan werken met meerdere PHP-versies in een enkele setup.
   - Het ondersteunt PHP-configuratierichtlijnen via .htaccess-bestanden.
   - Veilig omdat scripts worden uitgevoerd als de domeineigenaar.
- **Nadelen:**
   - Het maakt niet alle LSAPI-mogelijkheden beschikbaar.
- **Te herkennen aan:** Server API - ?

Op een lokale laptop of desktopcomputer kun je mod_php gebruiken, maar je moet mogelijk de Apache-gebruiker instellen op je eigen gebruikersnaam en het document root wijzen naar een locatie in je eigen bestandsruimte. Anders krijg je problemen met bestands- en maprechten.

Bij een hostingservice moet je een van de FastCGI-alternatieven of LSAPI gebruiken. Hostingservices kunnen je een keuze bieden.

*Vertaald door openai.com*

