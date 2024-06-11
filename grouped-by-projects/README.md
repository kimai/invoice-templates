# Invoice Template: Grouped By Projects

This template is based on din5008-invoice. 
For my invoices, it is necessary to provide the client with a breakdown of individual projects and activities performed. 
It's not the prettiest loop I use for this, but it works ;-).

![Screenshot of template](screenshot.png "Screenshot of template")

## Customization

Most values are taken from the Invoice template configuration:
- `Address` used in header and footer
- `Contact` is used as the introduction text of the invoice (supports markdown)
- `VatID` is used in the upper right corner (invoice details) as sender VAT
- `Title` is used in the upper right corner (invoice details) as invoice number title
- `Terms of payment` - used at the end of the invoice
- `Bank account` - used in the footer of the invoice

Company name is used from te global System configuration at `System -> Settings -> My company`.

Basic changes to the layout can be made in the following lines.
The highlight color is applied to the header and footer lines.
The suppress color is used by the template in various places.

```twig
{% set tagline = 'Your company slogan' %}
{% set highlight = '#008000' %}
{% set suppress = '#424242' %}
```

If available, the logo specified under `System -> Settings -> My company` is used.

The template creates an invoice in A4 format with the file name `YYYY-MM-DD_invoice-number_customer.pdf`. 
This can be customized in these configuration lines:

```twig
{%- set filename = invoice['invoice.date']|date('Y-m-d') ~ '_' ~ invoice['invoice.number']|replace({'/' : '-'}) ~ '_' ~ invoice['customer.company']|default(invoice['customer.name'])|replace({' ' : '-'}) -%}
{%- set option = pdfContext.setOption('filename', filename) -%}
{%- set option = pdfContext.setOption('format', 'A4-P') -%}
```

## Group-By feature

It is not quite easy to group by projects. 
My workaround is to iterate through a maximum number of projects. 
If more projects than this value are calculated in one invoice, the template turns off the grouping. 
The default value is 50, which should be more than sufficient. 
It can be changed in this line: 

```twig
{% set groupByMaxProjects = 50 %}
```

## Expenses and other positions

Anything that is not a timesheet entry is listed at the end of the list as expenses. 
This feature requires either the Expenses module or the use of the cloud version of Kimai.
