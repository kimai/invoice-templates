# Kimai Invoice-Templates

A place for sharing your Kimai invoice templates with the community, a place to find ideas.

Default Kimai invoice templates can be found [in the core repository here](https://github.com/kimai/kimai/tree/main/templates/invoice/renderer).

## List of all templates

### PDF

- [DIN 5008 compliant template](din5008-invoice)
- [Invoice grouped by projects](grouped-by-projects)

### HTML

- [Example](html-example)

### Docx

- [Company invoice](docx-company)
- [Project invoice](docx-project)

### Excel

- [Excel letter](xlsx-letter-de)
- [Basic spreadsheet](xlsx-simple)

### CSV

- [Export](export)

### OpenOffice Spreadsheet

- [Basic spreadsheet](oo-spreadsheet)

### Programmatic

- [JSON](data-transfer)
- [XML](data-transfer)
- [TEXT](data-transfer)

This one is a bit special, it is a XML document to generate the X-Rechnung format, which is required in the EU:

- [X-Rechnung](xrechnung)

## Installation

If not existing, create the directory `var/invoices/` in your Kimai installation.

```
cd /var/www/kimai/var/
mkdir invoices
```

Then copy the files from any subdirectory into this new directory (`/var/www/kimai/var/invoices/`).

They should show now up in your "Invoice templates" administration, in the **"Invoice document"** dropdown.

Please read the official documentation at [https://www.kimai.org/documentation/invoices.html](https://www.kimai.org/documentation/invoices.html) to find out more about building your own invoice templates.

## Sharing your template

- Fork this repository
- Create a new branch
- Add a new subdirectory with a unique name of your template
- Add a `README.md` file explaining your template
- Add a `screenshot.png` (or .jpg) image if possible
- Add the template file to the directory
- Edit the main [README.md](https://github.com/kimai/invoice-templates/blob/main/README.md) and add a link to your new directory under the appropriate format section
- Commit and Push your changes
- Open a PR
- Wait for feedback and merge 😃

By submitting your template you accept that it will be shared under the MIT license.
