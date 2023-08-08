# digital-response-generator
WordPress plugin generating member directory with Neon CRM API

Written by Benny Mattis for Catholic Volunteer Network

## Purpose

Generates a directory of member programs by combining uploaded static pages with data retrieved from Neon CRM database.

##How to Use

Link to download dynamically generated directory using shortcode [digital_response_link]. 

Incorporates static pages using most recent media uploads titled digital-response-section-1, digital-response-section-2, etc. Update sections by uploading pdfs with the same title.

Footer with page number is excluded from ads (i.e. the first two pages of digital-response-section-1, and every page of all subsequent static sections).

Override PDF generation by uploading a pdf directory to the media library titled digital-response-replacement. 

##Features

Refreshes file daily for new listings (upon site visit), and refreshes file whenever an attachment is uploaded, edited, or deleted with a title containing "digital-response." 
