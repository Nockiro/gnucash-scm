# gnucash-scm

## What is it?
In this repository I want to collect GnuCash reports/templates (written in [Guile Scheme](https://en.wikipedia.org/wiki/GNU_Guile)) that I've created or modified for myself and which I think can be useful.

### invoice.scm
Since the default gnucash reports are (in my opinion) very helpful, but lack a bit in their design, I wanted to create a template that I myself can use to some extend.  
The file and its corresponding css-file (for use in GnuCash report settings) are the result of that.  

Disclaimer: The design itself is based on an earlier version of the [InvoiceNinja v4 Bold Theme](https://invoiceninja.github.io/).

#### Screenshot
<img src="https://github.com/Nockiro/gnucash-scm/raw/master/readme-img/invoice-scm.png" height="512">  
(Click to view full-size image)

#### TODO
1. The CSS relies in some places on my own currently used invoice table configuration (Description, Quantity, Price, Total).  
That makes some rules obsolete when used with another configuration.

## Why is it?
In the past, I've sometimes modified templates in a "hacky" way - that is neither good for myself (updates tend to kill changes in the source folder) nor is it helpful for anyone else.  
With this repository, I want to counteract both.  
Disclaimer: I don't have much experience with creating templates, so there might be simpler solutions to some problems.

## How to use it
This repository is based on the assumption that you're running GnuCash version 4.6 or later.

You can read detailed instructions [on the GnuCash Wiki](https://wiki.gnucash.org/wiki/Custom_Reports#Loading_Your_Report), but basically (with the example of invoice.scm) it comes down to this:

1. Save the invoice.scm file on your GNC_DATA_HOME
  - At the time of writing, that's one of the following folders:
    - Linux: /home/`<username>`/.local/share/gnucash
    - Windows: %APPDATA%\GnuCash
    - macOS: /Users/`<username>`/Library/Application Support/GnuCash/
2. Create or modify the file `config-user.scm` in your GNC_CONFIG_HOME
  - At the time of writing, this is the same path on every OS except for Linux, there it's 
    /home/`<username>`/.config/gnucash
  - Add the content `(load (gnc-build-userdata-path "invoice.scm"))`  
    Feel free to rename the file as it might get confused with the original invoice.scm
3. Restart GnuCash. You should see the new report ("HTML-exportable invoice") in the menu along with the originals.
4. When using the report, make sure you have a look at the added options, e.g. "Hide zero-value amounts/sum" for title rows.
5. Look at the usage notes below to make sure you get the correct result.

### Usage notes
* This report is intended to be used as HTML export ("export" in the menu) which you can then print as PDF.
The PDF export from GnuCash seems to render the document different than browsers do.
* When printing as PDF in your browser, make sure the orientation is **not** set to landscape!
* The report works best if you use the settings listed in the header of [invoice.css](invoice.css)
* To fill the box at the right-hand side of the page, the invoice has to be posted/booked.
* Tip: You can customize your invoice entries (as seen in the screenshot) with HTML.