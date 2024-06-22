<!-- Filename: Potential_backward_compatibility_issues_in_Joomla_4 / Display title: Potentiële terugwaartse compatibiliteitsproblemen in Joomla 4 -->

<img
src="https://docs.joomla.org/images/thumb/e/e5/Quill_icon.png/30px-Quill_icon.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/e/e5/Quill_icon.png/45px-Quill_icon.png 1.5x, https://docs.joomla.org/images/thumb/e/e5/Quill_icon.png/60px-Quill_icon.png 2x"
data-file-width="71" data-file-height="59" width="30" height="25"
alt="Quill icon.png" />Content is Incomplete

This article or section **is incomplete, which means it may be lacking
information.** You are welcome to assist in its completion by editing it
as well. If this article or section <a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Potential_backward_compatibility_issues_in_Joomla_4/nl&amp;action=history"
class="external text" target="_blank" rel="noreferrer noopener"></a> <a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Potential_backward_compatibility_issues_in_Joomla_4/nl&amp;action=history"
class="external text" target="_blank" rel="noreferrer noopener">has not
been edited in several days</a>, please consider helping complete the
content.
<span class="small">This article was <a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Potential_backward_compatibility_issues_in_Joomla_4/nl&amp;diff=cur"
class="external text" target="_blank" rel="noreferrer noopener">last
edited</a> by
FuzzyBot
(talk\|
contribs
5 months ago. *(<a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Potential_backward_compatibility_issues_in_Joomla_4/nl&amp;action=purge"
class="external text" target="_blank"
rel="noreferrer noopener">Purge</a>)*</span>

Dit document volgt potentiële terugwaartse compatibiliteitsproblemen
voor Joomla! 4. Potentiële compatibiliteitsproblemen met extensies
worden opgesomd.

De basis voor deze vergelijking is Joomla! 3.10.

## Herziene systeemvereisten

De systeemvereisten zijn als volgt bijgewerkt:

- PHP 7.2.5
- MySQL 5.6
- PostgreSQL 11.0
- Ondersteuning voor SQL Server is vervallen.

### PHP MySQL Extensie

- Joomla ondersteunt niet langer de PHP ext/mysql driver (die verwijderd
  is in PHP 7.0). Joomla zal automatisch proberen de mysqli extensie te
  gebruiken (beschikbaar sinds PHP 5.3). Indien deze niet gevonden wordt
  zal er geen connectie met de database gemaakt kunnen worden.
- Strict modus is geactiveerd. De volgende flags zijn nu standaard
  actief in Joomla 4 en u moet misschien uw database queries
  overeenkomstig bijwerken. Dit helpt ons bij toekomstige MySQL versie
  upgrades en komt ook dichter bij Postgres zodat een betere
  comptabiliteit ontstaat tussen queries in beide talen.
    'STRICT_TRANS_TABLES',
    'ERROR_FOR_DIVISION_BY_ZERO',
    'NO_AUTO_CREATE_USER',
    'NO_ENGINE_SUBSTITUTION',

Als gevolg gebruikt Joomla 4 alleen **NULL date defaults**. Het gebruik
van de *invalid default date* van 0000-00-00 00:00:00 in Joomla 4 is
verouderd.

### PHP Postgres extensie

- Joomla! ondersteunt niet langer de ext/pgsql driver van PHP. Joomla!
  zal automatisch proberen om de PostgreSQL PDO driver (beschikbaar
  sinds PHP 5.3 en Joomla! 3.9) te gebruiken. Anders kan Joomla! geen
  verbinding met een Postgress database maken.

### PHP GMP extensie

This is required for using the  WebAuthn Passwordless
Login
feature. Note the PHP GMP Extension is installed by default on the
majority of hosting sites. The  WebAuthn Passwordless
Login
System Plugin is enabled by default in Joomla 4 on https sites.

### PHP mcrypt Extension

This is required for using the Joomla\CMS\Crypt\Cipher\CrytoCipher class
and its alias JCryptCipherCrypto.

## CMS bibliotheken

De volgende wijzigingen zijn gemaakt in de Joomla! CMS bibliotheken (dit
is hoofdzakelijk code gevonden in de \`libraries/cms\` map in Joomla!
3).

### Installatie

- Plugin installatie via de 'ontdekken' methode zoekt niet langer naar
  xml bestanden in de Joomla! 1.5 plugin folder layouts.
- In 3.x, only plugins scripts have the preflight method called and none
  make postflight available during the uninstall process. All extensions
  types will have these hooks available in 4.0 when being uninstalled.
  If you currently preflight and postflight and assume they only apply
  in an install/update context - this logic is now incorrect and you
  should use the install route (given as one of the method parameters)
- Bij het verwijderen van een plugin zal de functie die de plugin
  verwijdert nu getriggerd worden voordat er SQL queries uitgevoerd
  worden. Dit is nu consistent met andere extensie types.

#### Verwijderde classes

De volgende classes zijn in Joomla! 4.0 verwijderd :

- JInstallerComponent (gebruik hiervoor JInstallerAdapterComponent)
- JInstallerFile (gebruik hiervoor JInstallerAdapterFile)
- JInstallerLanguage (gebruik hiervoor JInstallerAdapterLanguage)
- JInstallerLibrary (gebruik hiervoor JInstallerAdapterLibrary)
- JInstallerModule (gebruik hiervoor JInstallerAdapterModule)
- JInstallerPackage (gebruik hiervoor JInstallerAdapterPackage)
- JInstallerPlugin (gebruik hiervoor JInstallerAdapterPlugin)
- JInstallerTemplate (gebruik hiervoor JInstallerAdapterTemplate)
- JSubMenuHelper (gebruik hiervoor JHtmlSidebar; let op dat dit in
  tegenstelling tot JSubMenuHelper, de toevoeging van een
  plaatsvervanger in uw template view nodig heeft)

#### JInstallerAdapter overerving

JInstallerAdapter no longer extends from JAdapterInstance and inherently
JObject.

Custom Installer Adapters must now be autoloaded.

### Menu

#### JMenu is nu een abstracte class

JMenu is nu een abstracte class. Subclasses van JMenu moeten nu ook een
load methode implementeren.

#### Handmatig include gedrag verwijderd

The logic in JMenu::getInstance() to manually include a file from the
application's includes/menu.php path has been removed. The JMenu
subclass should be autoloaded instead.

#### JMenuItem

- You can no longer retrieve the params property from JMenuItem
  directly. Use the getParams() method instead (available since Joomla
  3.7)
- JMenuItem::set and JMenuItem::get have been removed. Properties must
  be explicitly named
- There is now a AdministratorMenuItem class which extends from MenuItem
  that contains extra public properties used for the Administrator menu
  item.

### Pagination

- The magic pagination functions *pagination_item_active*,
  *pagination_item_inactive* have been removed. Use the JLayout's
  joomla.pagination.link instead
- The magic pagination function *pagination_list_render* is deprecated.
  Use the JLayout joomla.pagination.list instead

### Pathway

#### Manual Include Behavior verwijderd

The logic in JPathway::getInstance() to manually include a file from the
application's includes/pathway.php path has been removed. The JPathway
subclass should be autoloaded instead.

### Router

#### Manual Include Behavior Removed

The logic in JRouter::getInstance() to manually include a file from the
application's includes/router.php path has been removed. The JRouter
subclass should be autoloaded instead.

#### Method Signature Changes

The attachBuildRule and attachParseRule are now typehinted to require
callables.

### JVersion

Ondersteuning voor het benaderen van de JVersion class constanten als
class eigenschappen wordt niet langer ondersteund. De constanten werden
in Joomla! 3.5 geïntroduceerd om te voorkomen dat de oude class
eigenschappen bewerkt konden worden.

De volgende verouderde constanten zijn verwijderd:

- JVersion::RELEASE
- JVersion::DEV_LEVEL
- JVersion::BUILD

### JHtml

- The register function in JHtml is now typehinted to require a
  callable. Subclasses of JHtml will now need to match this signature
  (note this was already required at the function code level already).
- JHtml::\_ no longer allows you to call non-public methods in JHtml
- JHtml::\_ is now a final method (you can no longer override it if you
  subclass JHtml) and its signature has changed to take advantage of
  modern PHP features (scalar and variadic typehints)
- JHtmlBootstrap::modal is verwijderd. Gebruik
  JHtmlBootstrap::renderModal daarvoor in de plaats.
- JHtmlSortablelist::sortable has been deprecated in favour of
  JHtmlDraggablelist::draggable - the old method acts as a proxy to the
  new method currently to facilitate the removal of jQuery UI from
  Joomla Core. All media assets relating to the original jQuery UI
  implementation have been removed.
- JHtmlBatch has been removed as all the code had been moved to layouts
  for template overrides. Use the JLayouts directly in your code.

### Updater

- We removed the deprecated integer client handling from the updater
  extension adapter class. Please use **site** and **administrator** now
  and not the integer values **0** / **1**.

## Platform

De volgende wijzigingen zijn gemaakt in de Joomla! CMS bibliotheken (dit
is hoofdzakelijk code uit de \`libraries/cms\` map in Joomla! 3).

### Access

- JAccess::\$assetPermissionsById and JAccess::\$assetPermissionsByName
  and JAccess::preloadPermissionsParentIdMapping have been removed
  without replacement. Since 3.6 we've used other methods and class
  properties to optimize the loading of assets. See the
  <a href="https://github.com/joomla/joomla-cms/pull/12850"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">JAccess bug fixes and optimizations
  pull request</a> to see the reasons for this deprecation.
- JAccess::getActions has been removed. Use JAccess::getActionsFromFile
  or JAccess::getActionsFromData instead.

### Toepassing

#### Verwijderde classes

De volgende classes zijn verwijderd in Joomla! 4.0:

- JApplicationWebRouter (gebruik hiervoor de \`joomla/router\` package)
- JApplicationWebRouterBase (gebruik hiervoor de \`joomla/router\`
  package)
- JApplicationWebRouterRest (gebruik hiervoor de \`joomla/router\`
  package)

All references to JSite and JAdministrator have been removed (these were
just class alias' since Joomla 3.2)

#### Verouderde Classes

De volgende classes zijn verouderd en staan ingeplandom in Joomla! 5.0
verwijderd te worden:

- JApplicationBase (gebruik Joomla\Application\AbstractApplication
  daarvoor in de plaats)

#### CLI/Web class wijzigingen

The JApplicationCli and JApplicationWeb classes have been recomposed to
extend from the Framework's Application package instead. This breaks
type checks for a JApplicationBase object. For forward compatibility, it
is recommended to check if application classes are an instance of
Joomla\Application\AbstractApplication (JApplicationBase has extended
this class since Joomla! 3.4).

Additionally, both of these classes are now abstract. Developers
implementing these classes must provide a *doExecute* method with their
application's logic.

The registerEvent method is now typehinted to require a callable for the
\$handler parameter.

Applications that want to support both Web and CLI Applications should
now typehint against the \Joomla\CMS\Application\\
CMSApplicationInterface - this contains common methods (some of which in
Joomla 3.x were only found in the JApplicationCms class) that can be
used by all code. It's strongly recommended any custom applications
(especially CLI applications) implement this interface to make
compatibility checks easier, simultaneously any typehints should use the
interface rather than a concrete class.

##### JApplicationCli

- Oud: JApplicationCli **→** JApplicationBase **→** 
  Joomla\Application\AbstractApplication
- Nieuw:
  JApplicationCli **→** Joomla\Application\AbstractCliApplication **→** 
  Joomla\Application\AbstractApplication

##### JApplicationWeb

- Oud: JApplicationWeb **→** JApplicationBase **→** 
  Joomla\Application\AbstractApplication
- Nieuw:
  JApplicationWeb **→** Joomla\Application\AbstractWebApplication **→** 
  Joomla\Application\AbstractApplication
- The legacy ways of calling JApplicationWeb::redirect have been removed
  - With a message and messageType parameters. (Call enqueueMessage
    separately.)
  - Passing in a true/false value as the 2nd/3rd parameters instead of a
    redirect code will give an InvalidArgumentException instead of
    defaulting to a 303.
- JApplicationWeb::\$singleValueResponseHeaders has been removed because
  the Framework Application will be internally using PSR-7 Response
  objects as of its 2.0 release. This changes how the headers data is
  stored so it is always a multi-dimensional array with each top level
  key being the header names and the value being an array holding all of
  the values for that header.

##### CMSApplication

- The \$\_clientId, \$\_messageQueue and \$\_name class properties have
  all been renamed to remove their underscore prefix.
- Implementeert nu CMSApplicationInterface
- If there is an error retrieving a Pathway, Router or Menu object using
  the respective methods, the exception will now bubble up rather than
  the method silently catching the exception and returning null.
- CMSApplication::getInstance will now additionally try to load the user
  object (using the loadIdentity function).
- CMSApplication::isSite and CMSApplication::isAdmin have been removed
  as with the addition of the ConsoleApplication and ApiApplication can
  give misleading results. Please use CMSApplication::isClient
  (available from
  <img src="https://docs.joomla.org/images/a/a7/Compat_icon_3_7.png"
  decoding="async" data-file-width="40" data-file-height="17" width="40"
  height="17" alt="Joomla 3.7" />). For more information please see
   Discover on which client your extension code is
  running.

##### JApplicationSite

De \$\_language_filter en \$\_detect_browser class eigenschappen zijn
hernoemd om de underscore prefix te verwijderen.

De verouderde methode JApplicationSite::getPageParameters is verwijderd
ten gunste van de alias JApplicationSite::getParams

##### JApplicationHelper

JApplicationHelper::parseXMLLangMetaFile is verwijderd zonder
vervanging.

### Archive

- The archive package has been removed in favour of the frameworks
  archive package. Note the API should remain unchanged.
- De afhandeling van Errors gebruikt nu Exceptions in plaats van JError.

### Client

\Joomla\CMS\Client\ClientWrapper has been removed. Use the static
methods in \Joomla\CMS\Client\ClientHelper

### Crypt

- JCrypt::hasStrongPasswordSupport has been removed without replacement
  as all PHP versions Joomla 4 matches will support strong password
  hashing.

#### Verwijderde classes

De volgende Ciphers zijn verwijderd in Joomla! 4.0:

- JCryptCipher3Des
- JCryptCipherBlowfish
- JCryptCipherMcrypt
- JCryptCipherRijndael256
- JCryptCipherSimple

Deze zijn verwijderd zonder vervanging. Gebruik JCryptCipherCrypto

#### Verwijderde Methods

- JCrypt::hasStrongPasswordSupport has been removed without replacement
  (this attempted to detect bcrypt polyfills on linux hosting but has
  always returned true since we required PHP 5.3.10 in Joomla 3.3)

### Cache

- JCacheController::get now requires a callable. As a result
  JCacheControllerCallback::call has been removed.
- JCacheStorage::test has been removed. Use JCacheStorage::isSupported
  instead
- The default storage engines are no longer manually loaded as they are
  now autoloaded
- JCacheControllerOutput::start en JCacheControllerOutput::end zijn
  verwijderd en niet vervangen.
- CacheLite opslag is verwijderd omdat deze niet compatibel is met PHP7
  (de minimum PHP versie voor Joomla! 4)
- Afhandeling van fouten gebruikt nu Exceptions in plaats van JError.

### Component

- \Joomla\CMS\Component\ComponentRecord breidt niet langer JObject uit.

### Document

#### Verandering in overerving

Van de volgende classes is de overerving veranderd:

- JDocumentError (now extends from \Joomla\Cms\Document\HtmlDocument
  instead of \Joomla\Cms\Document\Document)

Note as a result of this change rendering an error page resets the
document object in Joomla\CMS\Factory::\$document, the rationale being
we want a clean document to work from; if the error page is triggered we
aren't interested in the metadata your component has set, or the media
added from some bad module, or whatever plugins are adding to the
display. We want a clean environment for rendering the error page only
containing the error page's loaded data.

#### Renderers

- In order to comply with the RSS feed specification,
  JDocumentRendererFeedRss now allows the lastBuildDate element to be
  configured using the JDocumentFeed::\$lastBuildDate class property
  when a feed is rendered. This value defaults to the current time, as
  is the case with Joomla! 3.x and earlier, however the time can be
  correctly set by changing this class property to a JDate object
  representing the desired timestamp.
- There is now a RendererInterface that all Renderers should implement
- JDocumentRenderer is now an abstract class and implements
  RendererInterface
- As an alternative to you can now individually load for metadata, for
  CSS and for JavaScript. The intention of this is to optionally allow
  users to place all JavaScript at the bottom of the HTML Document in
  their templates.

#### JDocumentFeed

The property type of JDocumentFeed::\$lastBuildDate has changed from a
string to a JDate object. The property was previously unused by the core
Joomla API but extensions may have used it.

### Database

- Deze package is vervangen door de Joomla Framework Database Package
- Debug modus is herschreven (zie de framework docs voor meer
  informatie). <a href="https://github.com/joomla-framework/database"
  class="external autonumber" target="_blank"
  rel="nofollow noreferrer noopener">[1]</a>)

### Factory

- Factory::getApplication no longer takes arguments. These were
  misleading as it always returned the active application after the
  first call in the bootstrap, whatever arguments were passed into the
  function.
- Factory::getXml is verwijderd, samen met JXMLElement. Gebruik daarvoor
  in de plaats rechtstreeks SimpleXMLElement.
- Factory:: getEditor is verwijderd. Gebruik JEditor::getInstance
  daarvoor in de plaats.
- Factory:: getUri has been removed use Uri::getInstance() instead.

### Environment

- JBrowser::isSSLConnection has been removed. Use
  JApplicationCms::isSSLConnection (available since Joomla 3.2)

### Bestandsysteem

- The filesystem wrapper classes have been removed. Continue using the
  original static methods.

### Filter

- JFilterInput::\_remove has been removed in favour of
  JFilterInput::remove
- JFilterInput::\_cleanTags has been removed in favour of
  JFilterInput::cleanTags
- JFilterInput::\_cleanAttributes has been removed in favour of
  JFilterInput::cleanAttributes
- JFilterInput::\_decode has been removed in favour of
  JFilterInput::decode
- JFilterInput::\_escapeAttributeValues has been removed in favour of
  JFilterInput::escapeAttributeValues
- JFilterInput::\_stripCSSExpressions has been removed in favour of
  JFilterInput::stripCSSExpressions

All of the above deprecations and removals are to allow the class to be
reunified with the framework parent class.

### Form

- The libraries/joomla/form/fields and libraries/joomla/form/rules
  directories are no longer registered to find form classes, all form
  classes should be autoloaded instead
- Two new properties added addfieldprefix which registers a namespace
  prefix for extensions (intended to be used as a replacement for
  addfieldpath). For example usage please see
  <a href="https://github.com/joomla/joomla-cms/pull/16419"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">this Github PR</a>
- JForm::getControlGroup is verwijderd. Gebruik het alias
  JForm::renderField (beschikbaar sinds Joomla 3.2.3).
- JForm::getControlGroups is verwijderd. Gebruik het alias
  JForm::renderFieldset (beschikbaar sinds Joomla 3.2.3).
- When rendering a field using the hiddenLabel option in JForm - it now
  only hides the label from the User Interface - the html is still
  rendered with the sr-only class for screen-reader accessibility
  purposes.
- JFormFieldUsergroup is verwijderd. Gebruik
  Joomla\CMS\Form\Field\UsergrouplistField daarvoor in de plaats
  (beschikbaar sinds Joomla 3.2).
- The Form class has removed the protected methods filterField() and
  validateField(). This will break any custom Form classes that extends
  core Form and use these methods. This has been replaced in favour of
  filtering at the field level (see
  <a href="https://github.com/joomla/joomla-cms/pull/12414"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">https://github.com/joomla/joomla-cms/pull/12414</a>
  for more information)

#### Fields

- JFormFieldFilelist and JFormFieldFolderList have had their filter
  properties renamed to `fileFilter` and `folderFilter` respectively (in
  order to allow the use of the regular Joomla filter attribute on
  returned values)
- JFormPredefinedlistField has its filter properties renamed to
  `optionsFilter` (in order to allow the use of the regular Joomla
  filter attribute on returned values)
- JFormFieldEditor::save has been removed without replacement
- JFormFieldText::getSuggestions has been removed in favour of
  JFormFieldText::getOptions

#### Media Field

The Media field type now encodes image metadata into the internal value.
This is a sample value:

images/banners/osmbanner1.png#joomlaImage://local-images/banners/osmbanner1.png?width=468&height=60

To produce the final Image URL or the relative image file path, you can
use the new helper:

echo \Joomla\CMS\HTML\HTMLHelper::cleanImageURL(\$oldValue);

To get the clean value (without adapter information and metadata) from
the value which is stored in media form field:

echo
\Joomla\CMS\Helper\MediaHelper::getCleanMediaFieldValue(\$oldValue);

Function cleanImageURL does not clean the image URL but returns object
where one part of the object is cleaned URL. Using echo throws an error.
For more information visit <a
href="https://github.com/joomla/joomla-cms/issues/35871#issuecomment-968107241"
class="external autonumber" target="_blank"
rel="nofollow noreferrer noopener">[2]</a>

### Wrapper

- The form wrapper classes have been removed. Continue using the
  original static methods.

### HTTP

#### Verouderde classes en interfaces

De volgende classes en interfaces zijn verouderd en staan op de
nominatie om in Joomla! 5.0 verwijderd te worden:

- JHttpResponse (gebruik Joomla\Http\Response hiervoor in de plaats)
- JHttpTransport (pas Joomla\Http\TransportInterface toe hiervoor in de
  plaats)

#### Verandering in de classes

The Framework's HTTP package is now included in Joomla! 4.0 and JHttp
and the JHttpTransport subclasses have been refactored to use the
upstream package.

##### JHttp

- JHttp no longer ships with a cacerts.pem bundle in the transports
  directory use the composer/ca-bundle instead which ships with core.

The JHttp class constructor has been loosened with the following
changes:

- The options parameter is no longer typehinted as a
  Joomla\Registry\Registry object, an array or any object implementing
  the <a href="https://secure.php.net/manual/en/class.arrayaccess.php"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">ArrayAccess</a> interface can be
  used instead
- The transport parameter now allows any Joomla\Http\TransportInterface
  object.

##### JHttpTransport

The now deprecated JHttpTransport interface extends
Joomla\Http\TransportInterface now and has caused backward compatibility
breaking changes in the interface. The constructor is no longer part of
the interface, and the interface's \`request()\` method has had a
signature change. Specifically, the second parameter which previously
typehinted the JUri class now typehints Joomla\Uri\UriInterface.

##### JHttpResponse

In refactoring the response object to inherit from the Framework's HTTP
package, which is now using the PSR-7 ResponseInterface API, a minor
compatibility break has been made in the structure of the response
headers. As of 4.0, this will now always be a multi-dimensional array
where the key is the header name and the value is an array of values for
that header (previously, this was a string).

### Afbeelding

#### Verouderde classes en interfaces

De volgende classes en interfaces zijn verouderd en voor verwijdering
ingepland voor verwijdering in Joomla! 5.0:

- JImageFilter (gebruik Joomla\CMS\Image\ImageFilter hiervoor in de
  plaats)
- JImageFilterBackgroundfill (gebruik
  Joomla\CMS\Image\Filter\Backgroundfill hiervoor in de plaats)
- JImageFilterBrightness (gebruik Joomla\CMS\Image\Filter\Brightness
  hiervoor in de plaats)
- JImageFilterContrast (gebruik Joomla\CMS\Image\Filter\Contrast
  hiervoor in de plaats)
- JImageFilterEdgedetect (gebruik Joomla\CMS\Image\Filter\Edgedetect
  hiervoor in de plaats)
- JImageFilterEmboss (gebruik Joomla\CMS\Image\Filter\Emboss hiervoor in
  de plaats)
- JImageFilterGrayscale (gebruik Joomla\CMS\Image\Filter\Grayscale
  hiervoor in de plaats)
- JImageFilterNegate (gebruik Joomla\CMS\Image\Filter\Negate hiervoor in
  de plaats)
- JImageFilterSketchy (gebruik Joomla\CMS\Image\Filter\Sketchy hiervoor
  in de plaats)
- JImageFilterSmooth (gebruik Joomla\CMS\Image\Filter\Smooth hiervoor in
  de plaats)

#### Class veranderingen

The classes from Framework's Image package have been inlined into CMS
and JImage and the JImageFilter subclasses have been refactored to use
them. I.e. all classes under Joomla\Image namespace moved to
Joomla\CMS\Image namespace.

### Menu

- JMenu::\$\_items, JMenu::\$\_default and JMenu::\$\_active have been
  had their underscore prefix's removed (note these properties were
  protected so this only affects custom subclasses of JMenu)

### New MVC Layer

- This has been removed in Joomla 4. We have decided that this effort
  was not successful and as a result have continued development work on
  the original MVC Layer (see the "Legacy MVC" section). There is a
  plugin located
  <a href="https://github.com/joomla-extensions/legacy-mvc"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">on GitHub</a> you can ship with
  your extensions whilst you migrate them back to the Legacy MVC (note
  that this is not shipped by default in Joomla 4).

### Keychain

Removing the keychain with 4.0 has resulted in the removal of the
following class:

- JKeychain

### Pathway

- JPathway::\$\_pathway and JPathway::\$\_count have been had their
  underscore prefix's removed (note these properties were protected so
  this only affects custom subclasses of JPathway)
- JPathway::\_makeItem has been removed in favour of JPathway::makeItem
  (note this method was protected so this only affects custom subclasses
  of JPathway)

### Profiler

- JProfiler::getmicrotime and JProfiler::getMemory have been removed in
  favour of the native PHP methods they wrapped (`microtime(1)` and
  `memory_get_usage()` respectively)

### Table

- JTable::\_\_construct database object is now typehinted to be a
  JDatabaseDriver.
  - Subclasses of JTable will need to ensure they are passing a
    JDatabaseDriver object to the parent constructor
  - Subclasses of JTable will need to change the method signature of
    setDbo() if they have an extended version of that method to include
    the typehint
- There is a new method JTable::hasField - all instances of
  property_exists on JTable instances will now use this proxy method
  instead to allow better interoperability of Table instances
- The JTableObserver pattern (and corresponding classes) has been
  removed from JTable. JTable now triggers events and Tags, Content
  History (and any other custom uses of this pattern) should move to
  standard plugins.

### Mail

De volgende methods zijn verwijderd in Joomla! 4.0:

- JMail::sendAdminMail is verwijderd

#### Exceptions

JMail no longer catches exceptions from PHPMailer. It is now the object
calling JMail's responsibility to handle these exceptions as
appropriate. In addition if mail sending is disabled in global
configuration calling `\ Joomla\CMS\Mail\Mail::send()` will throw a
`\Joomla\CMS\Mail\Exception\MailDisabledException`.

## Talen

- The functions setTransliterator, setPluralSuffixesCallback,
  setIgnoredSearchWordsCallback, setLowerLimitSearchWordCallback,
  setUpperLimitSearchWordCallback and
  setSearchDisplayedCharactersNumberCallback are now typehinted to
  require a callable.
- The `"_QQ_"` placeholder for double quotes has been removed (this only
  existed to work around an old PHP Bug that has been fixed). Escape
  double quotes if required (i.e. `\"`)
- The format for language file names has been changes to ease the work
  in 3rd party translation tools (such as crowdin). INI language files
  no longer have to contain the language code (i.e.
  en-GB.com_contact.ini =\> com_contact.ini), in this case the special
  case of en-GB.ini has been renamed to joomla.ini in the core language
  pack. en-GB.xml has been named langmetadata.xml. There is a b/c layer
  that will continue to read the old Joomla 3 file names throughout
  Joomla 4.
- \Joomla\CMS\Language\Multilanguage::getSiteLangs has been removed. Use
  \Joomla\CMS\Language\LanguageHelper::getInstalledLanguages(0) instead
- JLanguage::exists has been removed. Use
  Joomla\CMS\Language\LanguageHelper::exists instead.
- The wrapper classes JTextWrapper, LanguageHelperWrapper and
  TransliterateWrapper have been removed. Continue to use the static
  methods they wrapped.
- The pdf_fonts handling/support for language packs
  (`language/pdf_fonts`) has been removed from the language installer
  (<a href="https://github.com/joomla/joomla-cms/pull/31288"
  class="external text" target="_blank"
  rel="nofollow noreferrer noopener">see GitHub PR #31288</a>).

### Legacy MVC Layer

#### Legacy Controller

- JControllerLegacy has been removed from the legacy layer, and we no
  longer intend to remove it or its subclasses in the near future.
- JControllerLegacy no longer extends JObject. Controllers should not
  call any of the methods contained in the JObject class.
- JControllerLegacy implements an interface for multiple task
  controllers
- JControllerLegacy::\_construct now takes additional arguments. If you
  were previously getting a Controller object through
  JControllerLegacy::getInstance you do not need to change your code.
  - Parameter 2: An optional MVCFactoryInterface instance
  - Parameter 3: An optional CMSApplicationInterface instance
  - Parameter 4: An optional Input instance
  - Parameter 5: An optional FormFactoryInterface instance
- JControllerForm now uses the StringInflector package to determine the
  list view. This should improve its ability to determine the list view
  of more view names. If extension developers find that their list view
  is no longer being found they should manually set the *view_list*
  class property in their controller.

#### Legacy View

- JViewLegacy has been removed from the legacy layer, and we no longer
  intend to remove it or its subclasses in the near future.
- JViewHtml has been split into two classes - AbstractView and HtmlView.
  Abstract view contains the logic for accessing models and getting the
  name of the view and is intended to be a base class for non-Html
  views. Html view contains the same logic as before.
- There are now two subclasses of JViewHtml -
  \Joomla\CMS\MVC\View\ListView and \Joomla\CMS\MVC\View\FormView
  designed to speed up the development of list and form views and reduce
  code duplication.

### Library

- JLibraryHelper::\_load has been removed. Use
  \Joomla\CMS\Helper\LibraryHelper::loadLibrary instead.

### Sessies

The session package has undergone a major refactoring to use the
Framework's Session package. This change primarily affects the internals
of the package; changes to the primary public API through the JSession
class are minimal.

### String

The old JString class alias has been removed. Use
\Joomla\String\StringHelper instead.

#### Verwijderde classes en interfaces

The following classes and interfaces have been removed in Joomla! 4.0:

- JSessionExceptionUnsupported
- JSessionHandlerInterface
- JSessionHandlerJoomla
- JSessionHandlerNative
- JSessionStorage
- JSessionStorageApc
- JSessionStorageDatabase
- JSessionStorageMemcache
- JSessionStorageMemcached
- JSessionStorageNone
- JSessionStorageWincache
- JSessionStorageXcache

#### JSession

JSession now extends from the Framework's Joomla\Session\Session class.
Many of the methods have a modified signature and a compatibility layer
exists to help with the transition.

##### Namespace parameter verouderd

The *get*, *set*, *has* and *clear* methods previously supported a
namespace parameter. This parameter is now deprecated. The namespace
should be prepended to the name before calling these methods.

##### JSession::clear() Repurposed

In the Joomla\Session\Session class, the *clear* method is used to clear
all data from the session store. In JSession, this method is used to
remove a single key. When this method is called with parameters, it will
call the new *Joomla\Session\Session::remove()* method.

##### JSession::getInstance() verouderd

The singleton *getInstance()* method has been deprecated. The session
object should be retrieved from the active application or the dependency
injection container instead.

##### Sessie handlers

In Joomla! 3.x and earlier, session handlers were represented by the
JSessionStorage class and its subclasses. In Joomla! 4.0, session
handlers are now implementations of Joomla\Session\HandlerInterface
(which is an extension of PHP's <a
href="https://secure.php.net/manual/en/class.sessionhandlerinterface.php"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">SessionHandlerInterface</a>. All
handlers which were supported in Joomla! 3.x are still available in 4.0
in addition to two additional handlers: a handler natively implementing
the APCu extension and a handler supporting Redis.

### Social Media bibliotheken

The facebook, github, google, linkedin, openstreetmap, mediawiki and
twitter packages have all been removed from the CMS.

### User

- JUser::getParameters has been removed. You can no longer retrieve all
  parameters for a user but instead use JUser::getParam to get
  individual parameters as required.

#### Helper

- JUserHelper::getCryptedPassword has been removed. Joomla 4 only
  supports hashing with the native PHP password_hash function (via
  JUserHelper::hashPassword (available since Joomla 3.2.1))
- JUserHelper::getSalt has been removed without replacement (it
  generated the hash's JUserHelper::getCryptedPassword which is now
  removed as above)
- JUserHelper::invalidateCookie, JUserHelper::clearExpiredTokens and
  JUserHelper::getRememberCookieData have been removed without
  replacement. They had been unused in core since Joomla 3.2 when their
  logic was moved into the Cookie Authentication Plugin
- JUserWrapperHelper has been removed. Continue using the original
  static methods in JUserHelper.

### Classes Removed Without Replacement

- JNode
- JTree
- JGrid
- JError (use native exceptions when error handling is required)

#### Utilities

#### Verwijderde classes en interfaces

The following classes and interfaces have been removed in Joomla! 4.0:

- JArrayHelper

use Joomla\Utilities\ArrayHelper; instead.

## Externe bibliotheken

The following changes have been made to the external libraries that
Joomla! packages and ships.

### PHPMailer

Joomla! 4.0 ships with PHPMailer 6. Please review the
<a href="https://github.com/PHPMailer/PHPMailer" class="external text"
target="_blank" rel="nofollow noreferrer noopener">GitHub repository</a>
for relevant changes.

### PHPUTF8

At Joomla! 3.4, the PHPUTF8 library lived in two locations in the
Joomla! package; \`libraries/phputf8\` and
\`libraries/vendor/joomla/string/src/phputf8\`. In Joomla! 4.0, the copy
of the library in \`libraries/phputf8\` has been removed. The
Joomla\String\StringHelper class exposes many of the library's functions
and the Composer autoloader definition imports much of the library as
well, however, if you need a feature that is not already included then
you should import the required functions from the
\`libraries/vendor/joomla/string/src/phputf8\` path.

### SimplePie

The SimplePie library is no longer included with Joomla! 4.0.

### jQuery

Joomla! 4.0 ships with jQuery 3. Please review
<a href="https://jquery.com/upgrade-guide/3.0/" class="external text"
target="_blank" rel="nofollow noreferrer noopener">the upgrading
guide</a> for relevant changes. Note that we are not including jQuery
Migrate anymore either. We recommend using it locally to help debug your
code if there are any issues.

### jQuery UI

jQuery UI has been removed from Joomla 4. Whilst it hasn't been
officially announced as dead, there hasn't been a release of jQuery UI
since 2016.

### Bootstrap

Joomla! 4.0 ships with Bootstrap 5. Bootstrap 2.3.2 has been removed,
however we have left some BS2 classes in to ease the migration (e.g. The
old BS2 element-invisible still exists for screenreaders)

### FOF

FOF 2.x has been removed.

## Templates

All the Joomla! 3 templates - ISIS and Hathor in the backend, and
Protostar and Beez in the frontend are no longer supported. The new 4.0
backend template is called Atum and the frontend template is called
Cassiopeia.

As a consequence, all extensions must migrate to the new Bootstrap 5
style, away from the current Bootstrap 2.3.2 implementation. For more
information about Bootstrap, visit the <a
href="https://getbootstrap.com/docs/5.0/getting-started/introduction/"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">Bootstrap 5</a> Website and the
<a href="https://getbootstrap.com/2.3.2/" class="external text"
target="_blank" rel="nofollow noreferrer noopener">Bootstrap 2.3.2</a>
Website.

- Joomla 4 will load the template favicon first rather than the one in
  the Joomla Root in keeping with the concept the template is the single
  source of truth.
- Frontend components and module views now use Block Element Modifier
  (BEM) class markup to make it easier for templates to support
  frameworks other than bootstrap. See the
  <a href="http://getbem.com/" class="external text" target="_blank"
  rel="nofollow noreferrer noopener">BEM Website</a> for more
  information on how to build similar classes.

There where also changes to options of the core components that you
should take a look at when your tempalte should support 3.x and 4.x at
the same time: <a
href="https://docs.joomla.org/J4.x:Changed_parameters_for_template_providers"
class="external free" target="_blank"
rel="noreferrer noopener">https://docs.joomla.org/J4.x:Changed_parameters_for_template_providers</a>

## Overige

- The *\$\_PROFILER* global variable has been removed. Use
  */Joomla/CMS/Profiler/Profiler::getInstance* instead.

### Media in Libraries

No media is allowed in the libraries root folder in the CMS. All assets
associated with Joomla libraries should be put in the media folder per
best practices. Direct access is blocked with a *.htaccess* and the
*web.config* file in the root of the libraries directory.

### Bin

Removing the keychain with 4.0 has resulted in the removal of the entire
Bin directory as it only contained keychain.

### Components

- All components have been namespaced and directories reworked
  accordingly. For more information about this read the tutorial on
  building a component in Joomla 4.
- com_admin profile view has been removed. (This appears to have been
  created historically due to issues accessing com_users. This is no
  longer the case so all user edits go through com_users edit user view
  in the backend.)
- com_actionlogs PHP 5.5 backfill code has been removed and accordingly
  `ActionlogsHelper::getCsvData()` is now type hinted to return a
  `Generator` object
- com_actionlogs CSV export headers have been changed to match the
  strings shown in the UI.
- Core components have had URL Routing 'Legacy' mode removed from Joomla
  3.7. You should either use your .htaccess file or the redirect
  component to fix any internal URLs that change. You can try the
  'Modern' mode in Joomla 3 by following the instructions
  here
- The MailTo component has been removed without replacement. If you used
  this functionality you will need to find an alternative component on
  JED.
- In com_contact 's frontend contact view - the contact property has
  been removed as it was a duplicate of the item property. We chose to
  keep \$this-\>item as it was consistent with that in the article and
  tag views. Template overrides will need updating to reflect this.
- The repeatable field in com_fields has been removed in favour of the
  new subform field. Data from repeatable fields is automatically
  migrated to the new subform field but is stored in a different format.
- The xreference fields have been removed from *\#\_\_contact_details*,
  *\#\_\_content* and *\#\_\_newsfeeds* as they were unused.

### Plugins

- The Gmail authentication plugin has been removed. For more information
  please read <a
  href="https://developer.joomla.org/news/724-removal-of-the-gmail-authentication-plugin-as-of-joomla-4-0.html"
  class="external text" target="_blank" rel="noreferrer noopener">this
  blog post</a>
- Google reCAPTCHA v1 support has been fully removed from the CAPTCHA
  plugin. This hasn't worked since Q2 2018. Google dropped support for
  it.
- The reCAPTCHA plugin now uses Google's official PHP library for
  CAPTCHA under the hood
- For plugins using the 3.x compatibility layer, the name result is a
  protected property for both input parameters and return values. For
  information on the new recommended approach to plugins please read
  S:MyLanguage/J4.x:Creating_a_Plugin_for_Joomla
- For plugins using the 3.x compatibility layer, for any type hints for
  events that require a class, that class **must** be autoloaded before
  the plugin is instantiated.
- The onContentBeforeSave event now requires the data parameter. This
  has been passed in \Joomla\CMS\MVC\Model\LegacyModel since 3.7 but is
  now passed in consistently by core extensions and used by the core
  Joomla content plugin.
- Returning before calling `parent::__construct()` in the constructor of
  a plugin is no longer supported to avoid queuing the plugin into the
  event dispatcher.
- *onUserBeforeDataValidation* is deprecated as an event in favor of
  *onContentBeforeValidateData* (The event was usable by all content
  types and was not specific to users. Note that both events will be
  called for the duration of Joomla 4. You should migrate your code to
  the new event when you no longer need to support Joomla 3.

### Plugins (Events)

- In Joomla 4, events whose name does not start with "on" no longer
  work. They don't even produce any error, so it's very hard to figure
  out why they don't work. This means that you need to overwrite both
  the names of functions in plugins and the names of their calls. For
  more information please read
  <a href="https://github.com/joomla/joomla-cms/issues/36062"
  class="external autonumber" target="_blank"
  rel="nofollow noreferrer noopener">[3]</a>

### Administrator Helpers

- JAdministratorHelper has been removed without replacement. (It's been
  merged into JApplicationAdministrator.)
- JSubMenuHelper has been removed without replacement. (Use JHtmlSidebar
  instead - available since 3.0.)
- JToolbarHelper has been moved to the main libraries directory.

### Modules

- The administrator module *submenu* has been removed.
- Logic of *Module Chromes* (module styles) in template files
  `html/modules.php` have been moved to `JLayout` files. `modChrome_x`
  functions in `modules.php` are no longer supported. See
  <a href="https://github.com/joomla/joomla-cms/pull/23570"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">https://github.com/joomla/joomla-cms/pull/23570</a>
  for details.
- *Module Chromes* (module styles) `modChrome_horz`, `modChrome_xhtml`,
  `modChrome_rounded` have been removed from template `system` without
  replacement.
- Module Class Suffixes have been renamed and standardized. These are
  now called Module Class and are appended to the list of classes in the
  Module Chrome. (They are no longer rendered in the module output
  itself.)

### Error afhandeling

- Joomla will now handle PHP's E_USER_DEPRECATED errors and pipes it
  into JLog - this is useful for handling deprecations in many 3rd party
  PHP Libraries (note it will block the page load if debug mode is
  enabled)
- Joomla\CMS\Exception\ExceptionHandler now only operates on Exceptions
  thrown in JApplication::execute. We now use Symfony's ErrorHandler
  when this fails or exceptions are thrown outside of this. We expect
  this to have minimal effect on most users and should give a more
  helpful message in many cases than the traditional "Error displaying
  the error page" error for users when things go very wrong.
- Joomla\CMS\Exception\ExceptionHandler is now format aware and will
  render errors in html, json, xml, feed or cli aware formats
- The Joomla\CMS\Exception\ExceptionHandler::render() signature is
  changed to include the Throwable typehint. Before 3.5 when PHP 7
  support was added this was typehinted as Exception, and since 3.5 has
  been typechecked in the code itself.

### Base Tag

Previous Joomla versions set a header tag of the current URL in the
frontend. This has been removed as it served no clear purpose.

### JavaScript

The *caption.js* file has been removed from Joomla. Use the native HTML
elements *figure* and *figcaption*. (You can look at JLayout in
*layouts/joomla/content/intro_image.php* for an example).

saveOrderAjax does not send complete form data (like it did in Joomla
3), only cid and order variable. This may be insufficient because some
extensions need more data for proper sorting - see:
<a href="https://github.com/joomla/joomla-cms/issues/36346"
class="external free" target="_blank"
rel="nofollow noreferrer noopener">https://github.com/joomla/joomla-cms/issues/36346</a>

### Namespacing

Class usage like *\$msg = JText::\_( 'Hello man!' );* can now use
namespacing. That would turn into *\$msg = Text::\_( 'Hello man!' );*.
To use namespacing, you need to add the proper namespace declaration.
This should be added after the *defined('\_JEXEC') or die;*.

To find out the proper namespace you can either follow the instructions
here: <a
href="https://groups.google.com/forum/#!topic/joomla-dev-general/1ua9zIqlcVc"
class="external text" target="_blank"
rel="nofollow noreferrer noopener">SO confused about namespace &amp;
enquemessage...</a> or use the generated file pdf reference file:
#### Namespace mapping and manifest file name

Automatic namespace mapping won't work with extension manifest files
named `manifest.xml`. See:
<a href="https://github.com/joomla/joomla-cms/issues/37750"
class="external free" target="_blank"
rel="nofollow noreferrer noopener">https://github.com/joomla/joomla-cms/issues/37750</a>
