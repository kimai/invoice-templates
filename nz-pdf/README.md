# New Zealand Invoice Templates

PDF invoice templates customized for New Zealand business requirements.

Based on the [default Kimai PDF template](https://github.com/kimai/kimai/blob/main/templates/invoice/renderer/default.pdf.twig).

Includes two variants:
- `nz-invoice.pdf.twig` - Standard invoice with full item descriptions
- `nz-invoice-no-desc.pdf.twig` - Simplified invoice showing only project and activity names

## Key Features

- **GST Compliance**: Uses "GST Number" instead of VAT ID throughout the template
- **NZ Date Format**: Dates displayed in dd MMM yyyy format (e.g., "22 Jan 2026")
- **Table Dates**: Item dates in ISO format yyyy/MM/dd for clarity
- **Prominent Payment Section**: Bank account details displayed in a highlighted box below the invoice table with payment reference
- **Enhanced Readability**: Larger header and footer text (12px) for improved legibility

## Customization

Most values are taken from the Invoice template configuration:
- `Address` - Company address (header and customer details)
- `Contact` - Contact information displayed in footer
- `Payment Details` - Bank account details shown in the payment information box
- `Payment Terms` - Additional payment terms (supports markdown)
- `VatID` - Used as GST Number
- `Title` - Invoice title in header

### Payment Information Section

The template includes a styled payment information box that displays:
- Bank account details
- Invoice number as payment reference
- Optional payment terms

This section appears below the invoice table with a gray background and border for prominence.
