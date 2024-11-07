<!-- Filename: J4.x:User_Actions_Log / Display title: Gebruikersactieslogboek -->

## Introductie

De logcomponent voor gebruikersacties (com_actionlogs) biedt een infrastructuur om een auditlogboek van websiteactiviteiten te maken. De acties die worden gelogd, kunnen door de sitebeheerder fijn worden afgestemd. Derden kunnen zich in de component integreren om aangepaste berichten toe te voegen of om de systeemverwerking van standaardbeheerderacties uit te laten voeren.

**Opmerking:** Alleen supergebruikers hebben toegang tot de logcomponent voor gebruikersacties.

## Gebruikersactie Logboek

Om de Gebruikersactie Logboeklijst te bekijken:

- Selecteer **Gebruikers → Gebruikersactie Logboek** vanuit het beheerdersmenu.

![gebruikersactie logboek lijstpagina](../../../en/images/users/user-actions-log-list.png)

Vanaf deze pagina heeft een Supergebruiker een globaal overzicht van alle gebruikersactiviteiten die op een site zijn uitgevoerd.

- Exporteer Geselecteerde als CSV: deze knop exporteert alleen de items die geselecteerd zijn in de zichtbare lijst.
- Exporteer Alles als CSV: deze knop exporteert alle records. De filters worden genegeerd.
- Verwijder: deze knop verwijdert de geselecteerde items.
- Logboek Wissen: deze knop verwijdert alle logboekvermeldingen.
- Opties: een configuratieformulier om de logboekopties in te stellen.

## Opties

Het formulier Opties voor Gebruikersactieslogboek stelt de Supergebruiker in staat om te selecteren welke gebeurtenissen gelogd moeten worden en of IP-adressen in de loggegevens moeten worden opgenomen.

![optiespagina voor gebruikersactieslogboek](../../../en/images/users/user-actions-log-options.png)

## Plugins

Het actie-logsysteem maakt gebruik van een aantal plugins:

### Actielog - Joomla

Wanneer ingeschakeld, registreert deze plugin de kernacties van gebruikers, inclusief acties zoals inloggen/uitloggen, artikel bijwerken, module toevoegen. De plugin heeft geen parameters.

### Systeem - Gebruikersactieslog

Wanneer ingeschakeld, definieert deze plugin het aantal dagen waarna de logs worden verwijderd. Een waarde van nul betekent dat de logs nooit automatisch worden verwijderd.

### Privacy - Actielogs

Wanneer ingeschakeld, exporteert deze plugin de gegevens van het actielog voor een privacyverzoek van een gebruiker.

## Module Laatste Acties

Deze module wordt alleen weergegeven aan Supergebruikers in het Home Dashboard.

![logboekmodule gebruikersacties](../../../en/images/users/user-actions-log-module.png)

## Hoe een extensie aan het systeem te koppelen

Voel je vrij om dit gedeelte te bewerken door het te verbeteren of te corrigeren.

### Componentinstallatiescript

Voeg de extensie toe aan de tabel (`#__action_logs_extensions`) zodat deze
zal verschijnen in de configuratie van Gebruikersactielogboeken.
```php
            $extension = 'com_mycomponent';
            $db = Factory::getDbo();
            $db->setQuery(' INSERT into #__action_logs_extensions (extension) VALUES ('.$db->Quote($extension).') ' );
            try {
                // Als het mislukt, zal het een RuntimeException werpen
                $result = $db->execute();
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Voeg de extensieconfiguratie toe aan de tabel (`#__action_log_config`) zodat
je actiedata worden vastgelegd.
```php
           $logConf = new stdClass();
            $logConf->id = 0;
            $logConf->type_title = 'transactie';
            $logConf->type_alias = $extension;
            $logConf->id_holder = 'id';
            $logConf->title_holder = 'trans_desc';
            $logConf->table_name = '#__mycomponent_transaction';
            $logConf->text_prefix = 'COM_MYCOMPONENT_TRANSACTION';

            try {
                // Als het mislukt, zal het een RuntimeException werpen
                // Voeg het object toe aan de tabel.
                $result = Factory::getDbo()->insertObject('#__action_log_config', $logConf);
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Natuurlijk is het het beste om wat controle uit te voeren om zeker te stellen dat het
record nog niet bestaat.

### Componenthelper

In dit voorbeeld wordt de componenthelper gebruikt om de opslag van
acties uit te voeren.
```php
       /**
         * Log details van transactie in logrecord
         * @param   object  $user    Bespaart opnieuw ophalen van de huidige gebruiker.
         * @param   int     $tran_id  De zojuist gemaakte of bijgewerkte transactie-id
         * @param   int     $id  Doorverwezen id-referentie van het formulier om te identificeren of het om een nieuw record gaat
         * @return  boolean True
         */
        public static function recordActionLog($user = null, $tran_id = 0, $id = 0)
        {
                // haal de componentdetails zoals het id op
            $extension =  MycomponentHelper::getExtensionDetails('com_mycomponent');
            // haal de transactiedetails op voor gebruik in het logboek voor gemakkelijke referentie
            $tran = MycomponentHelper::getTransaction($tran_id);
            $con_type = "transactie";
            if ($id === 0) { $type = 'Nieuw '; } else { $type = 'Bijwerken '; }

            $message = array();
            $message['action'] = $con_type;
            $message['type'] = $type . $tran->tran_type . ' - '.$tran->tran_desc . ' $' . $tran->tran_amount;
            $message['id'] = $tran->id;
            $message['title'] = $extension->name;
            $message['extension_name'] = $extension->name;
            $message['itemlink'] = "index.php?option=com_mycomponent&task=transaction.edit&id=".$tran->id;
            $message['userid'] = $user->id;
            $message['username'] = $user->username;
            $message['accountlink'] = "index.php?option=com_users&task=user.edit&id=".$user->id;

            $messages = array($message);

            $messageLanguageKey = Text::_('COM_MYCOMPONENT_TRANSACTION_LINK');
            $context = $extension->name.'.'.$con_type;

            $fmodel = MycomponentHelper::getForeignModel('Actionlog', 'ActionlogsModel');

            $fmodel->addLog($messages, $messageLanguageKey, $context, $user->id);

            return true;
        }

        /**
         * Haal het model van een andere component voor gebruik
         * @param   string  $name    De modelnaam. Optioneel. Standaard mijn eigen voor veiligheid.
         * @param   string  $prefix  De klassenprefix. Optioneel
         * @param   array   $config  Configuratiearray voor model. Optioneel
         * @return object   Het model
         */
        public function getForeignModel($name = 'Transaction', $prefix = 'MycomponentModel', $config = array('ignore_request' => true))
        {
            \Joomla\CMS\MVC\Model\ItemModel::addIncludePath(JPATH_ADMINISTRATOR . '/components/com_actionlogs/models', 'ActionlogsModelActionlog');
            $fmodel = \Joomla\CMS\MVC\Model\ItemModel::getInstance($name, $prefix, $config);

            return $fmodel;
        }
```
### Front-end Transactieformulier

Nu de basis is gelegd, hoeven we alleen nog het proces te activeren.
We leggen informatie vast over een transactie die wordt gemaakt of
bijgewerkt en we hebben een model genaamd `transactionform.php`. Het is in de
Opslaan-methode dat we een logboek willen vastleggen.
```php
       // Dus de code boven dit punt controleert en doet wat het zou moeten doen en dan, na het succesvol opslaan van het record, controleren we de parameterinstelling om te zien of loggen vereist is en geven we belangrijke elementen door aan recordActionLog.
            $table = $this->getTable();

            if ($table->save($data) === true) {

                /* ---------------------------------------------------------------- */
                // trigger transactielog als nodig
                $act_log = $params->get('act_log', 0);
                if ($act_log && $table->id) {
                    // verzamel informatie en log in een nieuw actielogrecord
                    MycomponentHelper::recordActionLog($user, $table->id, $data['id']);
                }
                /* ---------------------------------------------------------------- */

                return $table->id;
            } else {
                return false;
            }
```
### Taalbestand

Tenslotte, om te helpen met de Actielogweergave aan de beheerderskant van
Joomla, willen we enkele belangrijke elementen van data instellen om in de
taalbestand nl-NL/com_mycomponent.ini te worden weergegeven.
```ini
    COM_MYCOMPONENT_TRANSACTION_LINK="Gebruiker {username} heeft een transactie aangemaakt ( {type} )"
```

*Vertaald door openai.com*

