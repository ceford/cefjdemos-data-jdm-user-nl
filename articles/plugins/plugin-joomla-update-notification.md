<!-- Filename: J3.x:Plugin_Joomla_Update_Notification / Display title: Joomla! Update Melding  -->

## Icoon en Taak

Er zijn twee plugins met vergelijkbare namen:

* **Quick Icon - Joomla! Update Notification**
* **Task - Joomla! Update Notification**

De eerste controleert op Joomla-updates en stelt je op de hoogte wanneer je de Home Dashboard-pagina bezoekt. Het heeft één parameter: de Groep van deze plugin (deze waarde wordt vergeleken met de groepwaarde die in Quick Icons-modules wordt gebruikt om iconen in te voegen).

De tweede controleert periodiek de beschikbaarheid van nieuwe Joomla! versies. Wanneer er een wordt gevonden, triggert het een taak om een update-herinneringse-mail naar Super Users te sturen. De e-mail kan worden aangepast via *Systeem → E-mailsjablonen*.

De e-mails die worden verzonden door de Joomla! Update Notification System plugins zijn bedoeld om te helpen de software up-to-date te houden, wat helpt om de website veilig te houden. Updates zouden zo snel mogelijk na de release moeten worden geïnstalleerd.

## Plugin Status

De twee aparte plugins kunnen elk Ingeschakeld of Uitgeschakeld zijn.

- Met **Quick Icon ... Uitgeschakeld** blijft het Home Dashboard *Checking Joomla ...* icoon inactief, hoewel je het kunt selecteren om naar de Joomla updatepagina te gaan.
- Met **Taak ... Uitgeschakeld:** wordt de taak om een e-mail te verzenden niet geactiveerd.

## Taak Parameters

Ga vanuit het Administrator-menu naar **Systeem / Geplande Taken** en selecteer het item **Update Notificatie** uit de lijst met *Geplande Taken*. Er zijn een aantal parameter- en informatietabbladen om te bekijken en indien nodig te wijzigen.

### Frequentie van Notificatie E-mails

De frequentie van taakuitvoering is standaard ingesteld op 24 uur. Dat betekent dat de Joomla-website om de 24 uur controleert op een update van de kern en alle extensies, plugins, modules en templates die zijn geïnstalleerd. Een waarde van 0 zou bij elke toegang tot de site een update-e-mail sturen. 0 is alleen voor testen!

Let op dat de taak wordt geactiveerd door siteactiviteit. Als u de enige gebruiker bent, wordt deze geactiveerd bij uw volgende bezoek als er meer dan 24 uur zijn verstreken.

### Supergebruiker E-mails

De e-mailnotificatie wordt alleen verzonden naar gebruikers met de Supergebruiker-privilege. Dit veld stelt u in staat om te selecteren welke Supergebruikers de e-mailnotificaties ontvangen.

- Als dit veld leeg is, ontvangen alle Supergebruikers van de site de update-notificatie e-mail.
- Om te beperken welke Supergebruikers de update-notificatie ontvangen, voert u hier de e-mailadressen van de Supergebruikers in. Als er meerdere e-mailadressen van Supergebruikers zijn, gebruikt u een komma om ze te scheiden.

### Taal van de E-mail

De notificatie kan worden verzonden in elke taal die u op uw website gebruikt.

- **Auto (standaard)** verstuurt de update-notificatie e-mail in de standaardtaal van de site.
- Een andere taal dan Auto (standaard) selecteren, dwingt de update-notificatie e-mails om in deze specifieke taal te worden verzonden.

## Tips

- Om Joomla! update-e-mailmeldingen uit te schakelen, schakelt u eenvoudigweg de plugin uit.
- De e-mail Onderwerp en Body-tekst kunnen worden aangepast via de
**Systeem / E-mailsjablonen** lijst. Selecteer het **Joomla: Update Notification** item. Op een meertalige site zal het in de momenteel geselecteerde taal zijn.
  - **Onderwerp** Let op de {SITENAME} – {URL} placeholders worden vervangen wanneer het bericht wordt verzonden.
  - **Body** Daar zijn ook meer placeholders!

*Vertaald door openai.com*

