<!-- Filename: Adding_an_image_to_an_article / Display title: Een afbeelding toevoegen aan een artikel -->

## Introduction

How best to add images to an article depends on which version of Joomla
and which editor are in use. This article has illustrations for Joomla
4, with notes on differences in Joomla 3, and TinyMCE the Joomla default
editor. To get started, open an article for editing:

- **Select** **Content **→** Articles** in the Administrator menu.
- **Select** the title of the article you wish to edit

After inserting the article text, place the cursor at the location where
the image should appear.

## Adding a local image

If the image is located in the images folder of your Joomla installation
you should insert the image using the **CMS Content **→** Media** button
In the TinyMCE edit toolbar (In Joomla 3: Select the Image button):

<img
src="https://docs.joomla.org/images/5/5e/Adding-an-image-to-an-article-cms-content-media.png"
decoding="async" data-file-width="1000" data-file-height="508"
width="1000" height="508" alt="Adding an image" />

In the popup window, navigate to the image you want to use and click to
select it. On selection a form will appear prompting for additional
data. In Joomla 4 the form is to the left. In joomla 3 the form is at
the bottom (scroll down):

<img
src="https://docs.joomla.org/images/d/d4/Adding-an-image-to-an-article-selected-image.png"
decoding="async" data-file-width="1000" data-file-height="508"
width="1000" height="508" alt="Selecting an image" />

1.  Stel de afbeelding eigenschappen naar behoefte in:
1.  - **Alternatieve tekst**: Dit wordt het **alt** attribuut va de
      afbeelding, een belangrijke functie voor toegankelijkheid en de
      naleving van web-standaards.

- **Image Class**: If an image is used without a caption some custom
  classes may be applied here. For example, in Joomla 4, **float-end
  ms-2 mb-1** will align the image to the right and float text around it
  with margins to the left and below to prevent text touching the image.
  In Joomla 3 the equivalent style is **pull-right**.
- **Figure Class**: If a caption is set then an alignment class, if any,
  should be applied to the Figure. It is a html tag that encloses the
  img tag. Note that in Cassiopeia margins are applied by the template
  style sheet.

1.  - **Caption**: Activeert het bijschrift, wat de titel onder de
      afbeelding toont.

**In Joomla 3**

1.  - **Uitlijning**: Stelt de afbeelding uitlijning in. Standaard is de
      uitlijning **Niet ingesteld**.
1.  - **Caption Class**: Koppelt de ingegeven class aan het *figcaption*
      element.
1.  Klik op de *Invoeg* knop om de afbeelding in te voegen. Het voeg
    afbeelding scherm sluit en de afbeelding wordt getoond in de editor.
    Of klik op de *Annuleren* knop om het 'voeg afbeelding toe' scherm
    te verlaten.

**Tip:** select the Toggle Editor button to see the applied Image and
Caption styles.

### Using Drag and Drop for Local images

In both Joomla 4 and Joomla 3 you can drag an image from the desktop or
a file browser directly into the article text and the image will be
uploaded to the media folder and placed in the article. The only snag is
that all such uploaded images will be placed in the same media folder.
The location of the Images Directory used for upload and whether this
feature is enabled (On by default) are set in the TinyMCE configuration
Options.

## Adding a remote image

If the image you wish to use is not in the images folder of your Joomla
installation a slightly different procedure is needed.

- **Select** **Insert **→** Image** from the TinyMCE toolbar to open a
  dialog box. In Jooml 3, use the Image icon and the same dialog as used
  for local images.
- **Insert** the image url in the Source field.
- **Fill out** the other fields as required.
- **Advanced** provides some formatting options applied as in-line
  styles. Experiment with 1rem, 2, groove. (This feature is incomplete)

<img
src="https://docs.joomla.org/images/3/39/Adding-an-image-to-an-article-insert-edit-image.png"
class="thumbborder" decoding="async" data-file-width="480"
data-file-height="477" width="480" height="477"
alt="Data for a remote image" />

### Using Drag and Drop for Remote images

You can drag and drop an image from a remote web site directly into your
article text. But be aware that this may also copy the image container
html with class statements not valid for your site.

## Het uploaden van afbeeldingen met behulp van de 'Invoegen afbeeldingen' scherm

U kunt ook nieuwe afbeeldingen uploaden door de upload sectie van het
'Invoegen afbeelding' scherm te gebruiken.

- First open the Media browser and navigate to the folder where you wish
  to store new images for the current article.

1.  Klik op de Bladeren knop om door bestanden te bladeren.
1.  Selecteer de afbeeldingen die u wilt uploaden. Klik op Openen om de
    selectie te bevestigen. Let op: De stijl en de lay-out van het door
    bestanden bladeren hangt af van de browser en het operating systeem
    dat u gebruikt.
1.  De geselecteerde bestand(en) verschijnen onderaan het 'Invoegen
    afbeelding' scherm. Klik *Upload starten* om het uploaden van de
    bestanden te beginnen.
1.  - Wanneer de upload voltooid is verschijnt een groen bericht
      bovenaan het scherm.
1.  U kunt nu de geüploade afbeelding selecteren en invoegen, zoals
    eerder beschreven.
