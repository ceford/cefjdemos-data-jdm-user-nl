<!-- Filename: How_to_debug_SMTP_mail_in_Joomla_4 / Display title: SMTP-mail en Gmail -->

## Invoering

Op de pagina Globale Configuratie, Serverpaneel is er een optie om een mailbezorgingsagent te selecteren. De standaardinstelling is *PHP Mail*. Als dit niet werkt, kan het zijn dat u wordt geadviseerd om SMTP te gebruiken. Dit gebruikt hetzelfde mechanisme als uw e-mailapplicatie. Er zijn verschillende instellingen die correct moeten zijn. In het kort:

Ga naar **Globale Configuratie** en selecteer de tab **Server**. Zoek naar het *Mail* paneel onderaan het formulier.

- **Mailer** instellen op SMTP. Er verschijnen verschillende velden.
- **SMTP-host** Standaard is dit localhost, maar het is onwaarschijnlijk dat dit werkt. Deze moet worden ingesteld op de host die uw uitgaande e-mail afhandelt, bijvoorbeeld een Gmail-account.
- **SMTP-poort** De standaardwaarde is 25. Controleer of dit de waarde is die uw SMTP-host verwacht.
- **SMTP-beveiliging** De standaard is *Geen*, maar waarschijnlijk hebt u STARTTLS nodig.
- **SMTP-authenticatie** Dit is mogelijk niet vereist als u een thuisnetwerk gebruikt waarbij uitgaande e-mails geen authenticatie vereisen. Anders:
- **SMTP-gebruikersnaam** en **SMTP-wachtwoord** voer de waarden in die u gebruikt om toegang te krijgen tot uw e-mailaccount via internet.
- Selecteer de knop **Verzend testmail**.

## Gmail Gebruiken

Als je een werkend Gmail-account hebt, kun je Gmail als je mailserver gebruiken door dit in de globale configuratie in te stellen.

Stel op het server-tabblad het volgende in:

- Mailer: SMTP
- SMTP Host: smtp.gmail.com
- SMTP Poort: 465
- SMTP Beveiliging: SSL/TLS
- SMTP Authenticatie: Ja
- Vul de volgende twee regels in met jouw informatie. Je moet een appspecifiek wachtwoord (ASP) gebruiken, zoals hieronder beschreven.
- SMTP Gebruikersnaam: jouw Gmail-gebruikersnaam
- SMTP Wachtwoord: het appspecifieke wachtwoord (ASP) dat je hebt gegenereerd, zoals hieronder beschreven.

De volgende combinaties werken ook:

- SMTP Poort 587
- SMTP Beveiliging: STARTTLS
- SMTP Poort 25
- SMTP Beveiliging: STARTTLS

De SSL-module hoeft niet te worden ingeschakeld in Apache.

De OpenSSL-extensie moet worden ingeschakeld in PHP. De details zijn te vinden op de [php.net Installatiepagina](https://www.php.net/manual/en/openssl.installation.php).

Als je WAMP op Windows gebruikt, is de openssl-module standaard niet ingeschakeld en moet je deze inschakelen. Om dit te doen:

1. Open het php.ini-bestand en haal de puntkomma `;` aan het begin van de regel `extension=php_openssl.dll` weg door deze te verwijderen.
2. Sla het php.ini-bestand op en herstart de Apache-service.

Let op dat als je 2-staps verificatie in Gmail gebruikt, je een nieuw wachtwoord moet toevoegen in Instellingen - Accounts - Accounts-instellingen wijzigen - Andere Google-accountinstellingen - Beveiliging - 2-staps verificatie - Beheer je appspecifieke wachtwoorden.

Wanneer het nieuwe appspecifieke wachtwoord (ASP) in groepen van vier tekens wordt gepresenteerd, gescheiden door spaties, zorg er dan voor dat je **de spaties NIET** invoert bij het SMTP-wachtwoord in de mailserverinstellingen in Joomla.

- Appspecifieke wachtwoorden (ASP's): Zie de Google Support-pagina getiteld [Inloggen met app-wachtwoorden](https://support.google.com/accounts/answer/185833).
- 2-staps verificatie: Zie de Google Support-pagina getiteld [2-staps verificatie inschakelen](https://support.google.com/accounts/answer/185839).

## Foutopsporing

Als de e-mail niet wordt verzonden of nooit aankomt:

- Selecteer **Plugins** in het **Home Dashboard → Sitepaneel**.
- Zoek en schakel de **System - Debug** plugin in en configureer deze:
- Stel **Toegestane Groepen** in op *Supergebruikers* om uitvoer van foutopsporing te beperken tot je eigen inlogsessie, zowel in de backend als de frontend. Als je niet wilt inloggen op de frontend als Supergebruiker, maak een unieke gebruikersgroep voor je testactiviteiten en selecteer die gebruikersgroep uit de lijst van toegestane gebruikersgroepen.
- **Opslaan & Sluiten**
- Selecteer **Algemene configuratie** in het **Home Dashboard → Sitepaneel**.
- Stel in het *Systeem* tabblad **Debug Systeem** in op *Ja*.
- Stel in het *Server* tabblad **Foutenrapportage** in op *Maximum*.
- Noteer in het *Logboek* tabblad de inhoud van *Pad naar logmap*, meestal *\[iets\]/administrator/logs*.
- Stel **Loggen van Bijna Alles** in op *Ja*.
- Stel in het *Aangepaste loggen* paneel het veld *Logcategorieën* in op *mail* (zonder aanhalingstekens).
- **Opslaan** om de debuginstellingen op te slaan.
- Selecteer in het **Server** tabblad de *Stuur Test E-mail* knop onderaan de pagina.

Als er problemen in de code optreden tijdens het testen, moet je een *Stack Trace* krijgen die jou of anderen kan helpen om het probleem te diagnosticeren. Zoek ook naar een bestand in de logmap met een naam als *administrator/logs/everything.php* en open het met een teksteditor. Dit kan helpen om te zien wat er werd gelogd toen het bericht werd verzonden.

*Vertaald door openai.com*
