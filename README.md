# digital-response-generator
WordPress plugin generating member directory with Neon CRM API

Written by Benny Mattis for Catholic Volunteer Network, using the Neon CRM API with FPDI and a modified version of TCPDF.  

A "pretty" version of these docs can be found at [https://wbmattis2.github.io/docs/digital-response-generator]

## Purpose

Generates a directory of member programs by combining uploaded static pages with data retrieved from Neon CRM database. Automates process of retrieving and inserting data about member organizations from the Neon database.  

## How to Use

### Upload static sections

Incorporates static sections using most recent media uploads titled digital-response-section-1, digital-response-section-2, etc. 

**Please Note** that this plugin identifies media uploads by their **title** in WordPress, rather than their URL or filename. Admins can view and edit an item's title by clicking on the item in the Media Library.

Update sections by uploading pdfs with the same title. E.g., change section 2 by uploading a newer pdf with the title digital-response-section-2.

All pages should be "statement" size (5.5in wide x 8.5in high) in portrait orientation.

Sections cannot be skipped: If PDFs entitled digital-response-section-1, digital-response-section-section-2, and digital-response-section-4 exist in the media library, then section 4 (and any subsequent sections) will be ignored until there is a pdf entitled digital-response-section-3 in the media library.

Section 1 should consist of a cover page, a full-page ad immediately following the cover page, and any number of subsequent pages containing introductory information.

Each subsequent digital response section should include any number of full-page (statement size PDF) ads. Usually there will be one or two ads in a given section. If a section has multiple pages, those pages will appear back-to-back in the generated PDF. The first section will be placed at the beginning of the generated PDF; the last section will be placed at the end, and any additional in-between sections will be dispersed among the listings.

### Table of Contents image

You can include an image to be placed above the table of contents by uploading it in .PNG or .JPG format to the media library. The image should be titled digital-response-contents-logo.

### Shortcode

Link to download dynamically generated directory by using shortcode ```\[digital_response_link\]``` in the contents of a Post or Page. This link is an anchor that can be styled with the class ```.digital-response-link```.

### Override PDF

Override the PDF generation process by uploading a pdf to the media library titled digital-response-replacement. Links created with the ```\[digital_response_link\]``` shortcode will then trigger a download of the file titled digital-response-replacement.

## Features

### Automatic refresh

Refreshes file daily for new listings (upon site visit), and refreshes file whenever an attachment is uploaded, edited, or deleted with a title containing "digital-response." Please note that refresh occurs only when somebody visits the site, e.g. if nobody visits the website for a week, then the file will not be refreshed during that time, but it will automatically refresh as soon as somebody visits the site (given that the plugin is installed and activated). This should be kept in mind if anyone intends to download an updated file directly without visiting the website.

### Footer excluded from select pages

Footer with page number is excluded from ads (i.e. the first two pages of digital-response-section-1, and every page of all subsequent static sections).

### Ignores test accounts

When gathering listings from the database, this plugin ignores any member organizations whose name includes the word " test " (case-insensitive), in order to avoid listing accounts created for NEON database testing purposes. If any member organizations in the future include the word " test " in their name, then test accounts in the NEON database will have to be marked differently, and this feature of the Digital Response Generator will have to be changed appropriately.  

## Troubleshooting  

### Why is the file refreshing at strange times?  

The directory is set to refresh on a daily basis, but it will only refresh when people visit the site. So, if it has been more than a day since anyone viewed the site, it will refresh when (and only when) someone views it. 

### I've uploaded files with the right file names. Why isn't the plugin refreshing the directory?  

The plugin identifies relevant files by their titles, rather than their file names. To view a document's title in the media library, click on the document and check the "title" field in the media preview screen.

### I made sure that the titles are correct, but the directory is still not being dynamically regenerated.  

Is there a file in your Media Library with the title "digital-response-replacement"? If so, then that file will serve as the directory, and the dynamic PDF generation feature will be overridden until that file is deleted or its title is changed. 

### The plugin still isn't working as expected.  

Please ensure that all of the static pages you have uploaded to your media library are .pdf files in "Statement" size and "Portrait" orientation. If you are using a Table of Contents image, ensure that it is a .png or .jpg file. If all else fails, feel free to contact me (Benny) with a description of the situation. Contact information can be found on [my GitHub profile](https://github.com/wbmattis2).



## Software Used  

[TCPDF](https://tcpdf.org/docs/license/) is available under the GNU Public License 3.0; [FPDI](https://www.setasign.com/products/fpdi/about/) is available to use under the MIT license.  

The version of TCPDF used in this plugin has been modified; some files unnecessary for the plugin's functionality have been removed, and line 21579 has been altered. The modification consisted of adding "-.35" to the $tw value assignment in the definition of addTOC(). Without this fix, the table of contents extends to the right edge of the page, ignoring the right margin. The fix limits the width of the table of contents so that it doesn't extend to the end of the page; this artificial margin can be adjusted by increasing or decreasing the extra value subtracted from $tw.  

## Special Thanks  

Special thanks to [Catholic Volunteer Network](https://catholicvolunteernetwork.org/) and [Perisphere Media](https://perispheremedia.com/) for their involvement and feedback in design, development, and deployment.  



