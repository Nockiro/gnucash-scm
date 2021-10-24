# gnucash-scm

## What?
In this repository I want to collect GnuCash reports/templates (written in [Guile Scheme](https://en.wikipedia.org/wiki/GNU_Guile)) that I've created or modified for myself and which I think can be useful.

### invoice.scm
Since the default gnucash reports are (in my opinion) very helpful, but lack a bit in their design, I wanted to create a template that I myself can use to some extend.
The file and its corresponding css-file (for use in GnuCash report settings) are the result of that. 

Disclaimer: The design itself is based on an earlier version of the [InvoiceNinja v4 Bold Theme](https://invoiceninja.github.io/).

#### TODO
1. I changed the "Article" and "Price" column hard-coded to something I needed. This should be adjustable via options.
2. The CSS relies in some places on my current invoice table design (Description, Amount, Price, Total). 
That makes some rules obsolete when used with another configuration.

## Why?
In the past, I've sometimes modified templates in a "hacky" way - that is neither good for myself (updates tend to kill changes in the source folder) nor is it helpful for anyone else.
With this repository, I want to counteract both.

## How?
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
