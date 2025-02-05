### Introduction

I thought, this could be of interest for those who need to create an e-invoice compliant to the European requirements (which are legally binding at least in Germany and France from 2025 on).

While I definitely wait for the plugin solution to be published (https://github.com/kimai/kimai/issues/1396) to allow for creating the e-invoice in a more elegant way, I had to find a solution as freelancer to create the e-invoices programmatically. 

The way I found feasible is in combination with the Invoice-Bundle plugin (https://www.kimai.org/store/invoice-bundle.html), which enables the generation of XML files.

### Solution

The solution is the following:
* Use this XML template file compliant with an e-invoice format; it allows for timesheet types "timesheet" and "expense"
* Define an invoice template in Kimai referencing the XML template
* Customize some of the invoice template fields to the e-invoice needs

In my approach I decided to place certain XML components in the Kimai template fields.

One needs:

In field "address":
```
<cbc:StreetName>StreetNameAndNumber 123</cbc:StreetName>
<cbc:CityName>Some City</cbc:CityName>
<cbc:PostalZone>12345</cbc:PostalZone>a
<cbc:CountrySubentity>Some province</cbc:CountrySubentity>
<cac:Country>
    <cbc:IdentificationCode>One of DE, FR, etc</cbc:IdentificationCode>
</cac:Country>
```

In field "contact":
```
<cbc:Name>Firstname Surnamer</cbc:Name>
<cbc:Telephone>+49 1501 123456</cbc:Telephone>
<cbc:ElectronicMail>prefix@postfix.eu</cbc:ElectronicMail>
```

In field "bank account":
```
<cbc:ID>IBAN number</cbc:ID>
<cac:FinancialInstitutionBranch>
<cbc:ID>BIC code</cbc:ID>
</cac:FinancialInstitutionBranch>
```

All other fields like "VAT-ID", "TAX rate", "Payment term in day" need to have reasonable entries. Field "Grouping of invoice lines" needs to be "Default (one row per entry)".

Select as invoice template the XML e-invoice template.

For the customer details to work for both (PDF document and e-invoice), it is assumed that the customer address has following logic:
```
StreetName
PostalCode CityName
```

If your logic deviates you have to adapt the template at the XML path "AccountingCustomerParty/Party/PostalAddress".

If you only want to send the XML file to the customer, you should first create a preview and check it with a suitable validator tool e.g. [OpenXRechnungToolbox](https://jcthiele.github.io/OpenXRechnungToolbox/resources/help/index.html) . If successful, create the final file.

In case you want to have both, a PDF file and an e-invoice XML file, you first create the PDF file in "preview" mode and afterwards the e-invoice file. That's because the unique invoice number is only available one-time...

By this procedure, many versions and details of the e-invoice definitions can be added as needed. Also, the x-rechnung 2.2.0 version is already quite old, but adaption to newer formats is straight forward.

Hope this helps!
