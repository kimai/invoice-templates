# Project-Grouped Invoice (with full timesheet detail)

A clean, letterhead-style PDF invoice template that groups line items by **project**,
while still showing every individual timesheet entry underneath — date, activity,
description, hours, rate, and amount.

Most of the built-in "grouped by project" options collapse each project into a single
summary line, which is great for a tidy invoice but throws away the detail some clients
want to see. This template gives you both: a bold project header row, followed by every
timesheet entry that belongs to it, then moves on to the next project.

## Preview

- Two-column header: your company address + logo on the right, aligned in one row;
  "Bill to" + invoice number/date/period directly below, same alignment
- Items table: `Date | Activity | Description | Hours | Rate | Amount`, grouped under a
  shaded project header row
- Footer: Subtotal, Tax (if applicable), and a bold Total with a single strong divider line
- Optional company logo, placed via absolute file path (see Installation)

## Installation

1. Copy `project-grouped.pdf.twig` into `var/invoices/` in your Kimai installation
   (create the directory if it doesn't exist yet).
2. If you want your logo in the header, place a PNG at a fixed path on your server (e.g.
   `/opt/kimai/public/images/your-logo.png` for the official Docker image) and update the
   `src` attribute in the template to match. Twig templates can't use `asset()` or other
   Twig functions here — Kimai's invoice renderer sandboxes most of them — so the image
   path has to be a plain, hardcoded absolute filesystem path.
3. Clear the cache: `bin/console cache:clear`.
4. In your invoice template settings, set **Document** to `project-grouped`.
5. **Important:** set **Calculation** to the option that creates *one row per timesheet*,
   not "grouped by project." The grouping in this template happens entirely in the Twig
   layout — if Kimai's own calculator pre-collapses entries by project first, you'll lose
   the per-entry detail before the template ever sees it.

## Notes

- Sizes and spacing use millimeters (`mm`) rather than pixels wherever precise physical
  sizing matters (e.g. the logo). mPDF, the HTML-to-PDF engine Kimai uses, can be
  inconsistent about honoring CSS/HTML pixel sizing on embedded images — absolute units
  avoid that entirely.
- Twig's `namespace()` function (commonly used elsewhere for accumulating totals across a
  loop) is blocked by Kimai's invoice-renderer sandbox, so this template doesn't compute
  per-project subtotals — only the invoice-level Subtotal/Tax/Total from Kimai's own
  calculation.
