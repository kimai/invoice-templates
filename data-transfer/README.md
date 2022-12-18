# Data transfer templates

Back to [main page](https://github.com/kimai/invoice-templates).

## Introduction

These templates are examples in case you plan to post-process invoices.

You can use [XML](xml.xml.twig), [JSON](javascript.json.twig) and a multi-line [TEXT](text.txt.twig) format.

You likely want to use them in combination with the invoice command (`bin/console kimai:invoice:create`) and 
then parse the output and e.g. batch process the generated JSON files. 

These templates need the additional renderers, which ship with the [invoicing plugin](https://www.kimai.org/store/invoice-bundle.html) (installed in the [Kimai-Cloud](https://www.kimai.cloud)).
